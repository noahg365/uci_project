# uci_project1
![network topology](https://user-images.githubusercontent.com/84607161/143983879-4ee45c00-efab-41b6-8b80-60e9c1d33dd8.png)
(Us-east-2) 

These files have been tested and used to generate a live ELK deployment on AWS. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yaml file may be used to install only certain pieces of it, such as Filebeat.

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load Balancing protects us from Ddos attacks and improves peformance for websites,databases,ect.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the events in data and system logs. 

The configuration details of each machine may be found below.

Name	Function	IP Address	Operating System

Jump Box	Gateway		172.31.10.31 Linux- AMI

Webserver1	Server	10.0.0.134	Linux- AMI

Webserver2	Server		10.0.2.15 Linux- AMI

ELK	Server	172.31.24.133	Linux- Ubuntu

Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the Personal Home IP.

Machines within the network can only be accessed by the Jump Box.

A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Addresses
Jump Box	172.31.10.31 Yes	Personal Home IP
Webserver1	No	10.0.0.134
Webserver2	No	10.0.2.15
ELK	No	172.31.24.133
Elk Configuration
Ansible automation helps with the representation (IAC). IAC involves provisioning and management of computing infrastructure and related configuration.

The playbook implements the following tasks:

The first step of the playbook is to install docker.io
The second step of the playbook is to increase virtual memory with the command sysctl -w vm.max_map_count=262144.
The third step of the playbook is to install pip with a present state.
The fourth step of the playbook is to install docker python module with a present state.
The fifth step of the playbook is to download and launch a docker web container with the image sebp/elk:761, a started state, and published ports of 5601, 9200, and 5044.
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

Docker-ps-output

Target Machines & Beats
This ELK server is configured to monitor the following machines:

Webserver1, IP 10.0.0.134
Webserver2, IP 10.0.2.15
The following Beats have been installed:

Filebeat
Metricbeat
These Beats allow us to collect the following information from each machine:
Filebeat collects logs it has been monitoring in specific location that was chosen.
Metricbeat collects metrics from the operating system and any services runnning on server.

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the playbook file to your ansible directory.
Update the config file to include your ELK's private IP address
http://[your.VM.IP]:5601/app/kibana is the url to check that vm is running.
