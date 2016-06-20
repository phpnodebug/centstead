require 'json'
require 'yaml'

VAGRANTFILE_API_VERSION = "2"

confDir = File.expand_path(File.dirname(__FILE__) + "/config");

configPath = confDir + "/config.yaml"
afterScriptPath = confDir + "/after.sh"

require File.expand_path(File.dirname(__FILE__) + '/scripts/centstead.rb')

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  Centstead.configure(config, YAML::load(File.read(configPath)))

  if File.exists? afterScriptPath then
    config.vm.provision "shell", path: afterScriptPath, privileged: false
  end
end