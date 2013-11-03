vagrant-oraclexe
================

Run Oracle XE 11g Release 2 as a ubuntu vagrant box, provisioned by ansible

Prerequisites
-------------

You need to have alien, vagrant, virtualbox, ansible available. Unfortunately, ansible is not available to windows, it's only for *nix now.

I'm going to provide the prerequisites installation steps on ubuntu here.

alien and virtualbox may be installed via simple 'sudo apt-get install alien virtualbox'.

vagrant can also be installed similarly ('sudo apt-get install vagrant'), but if you would like to have newer version, you may download the latest version from [Vagrant - Downloads](http://downloads.vagrantup.com/).

ansible can be installed by following the instructions [here](http://www.ansibleworks.com/docs/intro_installation.html).

You also needs to download Oracle XE 11g release 2 from [oracle](http://www.oracle.com/technetwork/products/express-edition/downloads/index.html).

Steps
-----

- Before you start up your vagrant vm, we need to preprocess the rpm into deb format so that ubuntu can install it.
  Please go to the downloaded zip and execute the following

  ```
  unzip oracle-xe-11.2.0.1.0.x86_64.rpm.zip
  cd Disk1/
  sudo alien --to-deb --scripts oracle-xe-11.2.0-1.0.x86_64.rpm
  ```

  Please copy the output file, oracle-xe-11.2.0-1.0.x86_64.deb, to <project>/provisioning/files

- cd <project>
- 'vagrant up'
- Wait and see if there's anything goes wrong.
- 'vagrant reload' to restart the vagrant box

By now the installation part is completed, but you'll have to configure your database manually. In the process Oracle XE will need to know your password, port number sort of information.

- 'vagrant ssh' to login to the vagrant box
- 'sudo /etc/init.d/oracle-xe configure', please make sure this is executed on the vagrant box.

That should do the trick. In case it doesn't, please let me know.

--
Douglas Liu: sohoffice at gmail dot com
