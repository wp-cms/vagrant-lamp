# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/xenial64"
    config.vm.network "private_network", ip: "192.168.33.10"
    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 1
    end
    config.vm.synced_folder ".", "/var/www", :mount_options => ["dmode=777", "fmode=666"]
    config.vm.provision "shell", path: "bootstrap.sh"
    config.vm.provision "shell", :run => 'always', inline: <<-SHELL
        
        echo -e "\n--- Start MySQL ---\n"
        sudo /etc/init.d/mysql start
        
    SHELL

end