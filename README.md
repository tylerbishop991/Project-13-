# Project-13-
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagrams/UntitledDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook file may be used to install only certain pieces of it, such as Filebeat.

![](Ansible/Filebeat.PNG)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive and avalible, in addition to restricting access to the network.
- Load balancers protect against distributed denial-of-service attacks by rerouting traffic to other avalible servers when a specific server becomes overloaded.
- Jump box provides a single point of connection to the network so the other virtual machines on the network are not exposed to the public internet. It will limit the security settings to a single machine instead of multiple machines such as:
  - Firewall host on jump box
  - log monitoring
  - two-factor authentication for SSH login to the jump box

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat monitors your servers by collecting metrics from the system and services running on the server, such as: Apache.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function      | IP Address     | Operating System |
|-----------|---------------|----------------|------------------|
| Jump Box  | Gateway       | 10.0.0.4       | Linux            |
| Web-1     | Web server    | 10.0.0.11      | Linux            | 
| Web-2     | Web server    | 10.0.0.12      | Linux            |
| ElkVM     | Elk server    | 10.1.0.4       | linux            |
| RedTeamLB | load balancer | 52.250.112.188 | linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the RedTeamLB machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 72.178.27.50

Machines within the network can only be accessed by SSH.
- The Jump Box was able to access the Elk machine through SSH. The IP address is 20.187.38.11

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Address |
|-----------|---------------------|--------------------|
| RedTeamLB | yes                 | 72.178.27.50       |
| Elk VM    | no                  | 20.187.38.11       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- This allows IT administrators to automate away the drudgery from their daily tasks. That frees them to focus on efforts that help deliver more value to the business by spending 
  time on more important tasks.

The playbook implements the following tasks:
- Installs docker.io with update_cache:yes
- Installs python 3-pip
- Increases virtual memory and tells the system to use more memory
- Downloads and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](Ansible/Elk761.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.11
- 10.0.0.12

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- We use Filebeat to collect, parse, and visualize ELK logs in a single command.
- We use Metricbeat to collect and monitor the services that are running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to the new install-elk.yml file created in your container in /etc/ansible
- Update the Hosts file to include 10.1.0.4ansible_python_interpreter=/usr/bin/python3 in the [elk] group.
- Run the playbook, and navigate to http://137.135.14.99:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
