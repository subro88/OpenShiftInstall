
Installation


Clone this repo

git clone https://github.com/subro88/OpenShiftInstall.git
Execute the installation script
cd installcentos
./install-openshift.sh
Automation
Define mandatory variables for the installation process
# Domain name to access the cluster
$ export DOMAIN=<public ip address>.nip.io

# User created after installation
$ export USERNAME=<current user name>

# Password for the user
$ export PASSWORD=password
Define optional variables for the installation process
# Instead of using loopback, setup DeviceMapper on this disk.
# !! All data on the disk will be wiped out !!
$ export DISK="/dev/sda"
Run the automagic installation script as root with the environment variable in place:
curl https://raw.githubusercontent.com/okd-community-install/installcentos/master/install-openshift.sh | INTERACTIVE=false /bin/bash
Development
For development it's possible to switch the script repo

# Change location of source repository
$ export SCRIPT_REPO="https://raw.githubusercontent.com/okd-community-install/installcentos/master"
$ curl $SCRIPT_REPO/install-openshift.sh | /bin/bash
Testing
The script is tested using the tooling in the validate directory.

To use the tooling, it's required to create file validate/env.sh with the DigitalOcean API key

export DIGITALOCEAN_TOKEN=""
and then run start.sh to start the provisioning. Once the ssh is connected to the server, the script will atatch to the tmux session running Ansible installer.

To destroy the infrastructure, run the stop.sh script.
