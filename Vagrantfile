$script = <<-SCRIPT
    apt-get update && apt-get install -y mysql-server-5.7 && \
    mysql -e "create user 'phpuser'@'%' indentified by 'pass';"
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"
    config.vm.network "forwarded_port", guest: 80, host: 8975
    config.vm.network "public_network", ip: "192.168.11.182", netmask:"255.255.254.0", bridge: "Intel(R) Ethernet Connection (7) I219-V"
    
    config.vm.provision "shell", 
        inline: "echo Hello, World!"
    config.vm.provision "shell", 
        inline: $script
    
    config.vm.synced_folder "./configs", "/configs"
    config.vm.synced_folder "." "/vagrant", disabled: true
end