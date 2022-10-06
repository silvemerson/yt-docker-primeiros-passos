# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_DISABLE_VBOXSYMLINKCREATE=1

vms = {
  'docker-host' => {'memory' => '3072', 'cpus' => 1, 'ip' => '10', 'box' => 'centos/7'}
}

Vagrant.configure('2') do |config|

  config.vm.box_check_update = false

  vms.each do |name, conf|
    config.vm.define "#{name}" do |yt|
      yt.vm.box = "#{conf['box']}"
      yt.vm.hostname = "#{name}"
      yt.vm.network 'private_network', ip: "172.27.0.#{conf['ip']}"
      yt.vm.provider 'virtualbox' do |vb|
        vb.memory = conf['memory']
        vb.cpus = conf['cpus']
   yt.vm.provision "shell", inline: <<-SHELL
     yum update -y

   SHELL

      end
    end
  end
end
