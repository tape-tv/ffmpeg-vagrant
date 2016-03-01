Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/trusty64'
  config.vm.provider 'virtualbox' do |v|
    v.memory = 2048
    v.cpus = 2
  end
  config.vm.network 'forwarded_port', guest: 7001, host: 7001 
  config.vm.provision 'apt', type: 'shell', inline: 'apt-get update -y'
  config.vm.provision 'git', type: 'shell', inline: 'apt-get install -y git'
  config.vm.provision 'yasm', type: 'shell', inline: 'apt-get install -y yasm'
  config.vm.provision 'x264', type: 'shell', inline: 'apt-get install -y libx264-dev'
  config.vm.provision 'ffmpeg', type: 'shell', inline: %Q{
    git clone https://github.com/FFmpeg/FFmpeg.git
    cd FFmpeg
    ./configure --enable-gpl --enable-libx264
    make
    make install
  }
end

