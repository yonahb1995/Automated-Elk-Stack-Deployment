# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Link to Network Diagram](https://github.com/Howmanylights/automated-elk-stack-deployment/blob/main/Diagrams/Network%20Diagram.pdf)

I used the following files to generate and configure the network pictured above. Additionally, these YAML files may be used to install and configure select pieces of the full network, such as metricbeat.

[Link to YAML Files](https://github.com/Howmanylights/automated-elk-stack-deployment/tree/main/Ansible)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

I created this network in order to expose and moniter a load balanced instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network. Additionally, a load balancer will help protect my webservers from overloaded traffic or other forms of denial of service attacks.

I've connected these webservers through a singular jumpbox in order to restrict general access. By configuring my network security groups, I've allowed access to the webservers via jumpbox *only*. Furthermore, I've also allowed access to the jumpbox via my local machine via ssh key pairings.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logs and system level cpu usage.
Filebeat will record system logs and centralize in our Kibana dashboard. Additonally, Metricbeat will moniter system cpu usage, memory, disk usage, and other system level processes.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jumpbox  | Gateway   | 10.0.0.4   | Linux            |
| ELK-VM   | ELK       | 10.1.0.4   | Linux            |
| Web-VM-1 | Webserver | 10.0.0.5   | Linux            |
| Web-VM-2 | Webserver | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumobox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 71.63.246.82.

Machines within the network can only be accessed by The Ansible Container within the Jumpbox. At the time of writing, this container holds a public IP of 104.42.188.201.

Note that both Public IP addresses are dynamic and subject to change.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accesible | Allowed IP Addresses |
|----------|--------------------|----------------------|
| Jumpbox  | No                 | 71.63.246.82         |
| Elk-VM   | No                 | 104.42.188.201       |
| Web-VM-1 | No                 | 104.42.188.201       |
| Web-VM-2 | No                 | 104.42.188.201       |

### Elk Configuration

I used Ansible to automate configuration of the ELK virtual machine. In lieu of manual configuration, automatic configurtation is advantageous due to how it allows me to scale up the network as large as I need to.

The playbook implements the following tasks:
- Installs docker.io, python3-pip, and the Docker module
- Increases virtual memory, and allows the system to access and use the increased virtual memory
- Downloads and launches the docker elk container, and enables the docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[Link to succesful `docker ps` command](https://github.com/Howmanylights/automated-elk-stack-deployment/blob/main/Images/dockerPS.PNG)

### Target Machines & Beats
I configured the ELK server to monitor the following machines:
- Web-VM-1
- Web-VM-2

I installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow me to collect the following information from each machine:
- Filebeat will allow me to moniter system log files and collect them into a convienent Kibana dashboard.
- Metricbeat will allow me to periodically collect metrics from systems and services running on the webservers.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
