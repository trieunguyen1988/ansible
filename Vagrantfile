Vagrant.configure("2") do |config|

    config.vm.box = "bento/ubuntu-16.04"
    config.ssh.insert_key = false

    config.vm.define 'yama' do |yama|
        yama.vm.hostname = 'yama-remote'
        config.vm.provider :virtualbox do |vb|
            vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        end
        yama.vm.network 'forwarded_port', guest: 80, host: 3388 
        yama.vm.network 'forwarded_port', guest: 443, host: 3443
        yama.vm.network 'forwarded_port', guest: 27013, host: 27013
        # Create a private network, which allows host-only access to the machine
        # using a specific IP.
        config.vm.network 'private_network', ip: '192.168.3.33'

        ENV['LC_ALL']='en_US.UTF-8'

    end
end
