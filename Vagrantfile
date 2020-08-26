# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box_check_update = false
  config.vm.box_url = [ 'https://otus.ru/media/c7.4.box' ]    
  config.vm.box = "c7.4"
  config.vm.hostname = "disks"
  config.vm.define "disks" do |d|
    d.vm.provider "virtualbox" do |vb|
      vb.name = "disks"
      vb.linked_clone = true
      (1..6).each do |n|
        disk_file = "./.vagrant/machines/disks/c7-disk-d#{n}.vdi"
        unless File.exists?(disk_file)
          vb.customize ['createmedium', 'disk', '--filename', disk_file, '--size', 500]
        end
        vb.customize ['storageattach', :id, '--storagectl',  'SATA', '--port', n, '--device', 0, '--type', 'hdd', '--medium', disk_file ]
      end
    end
  end
end
