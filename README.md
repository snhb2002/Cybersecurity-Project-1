# Cybersecurity-Project-1
Cybersecurity Project 1
## Automated ELK Stack Deployment

These files were used to configure the network below in this repository.


![Netwrok_Diagram](https://github.com/snhb2002/Cybersecurity-Project-1/blob/f2e27114ed36cc4ba8bc79797a9e0551c8acebe6/diagrams/Network%20Diagram.png)

The files below were tested and applied to make a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Metricbeat.

## Install ELK Servers
[install-elk.yml](https://github.com/snhb2002/Cybersecurity-Project-1/blob/9c406f0f6d5b852a5c84c6e1208a56015725b233/ansible/install-elk.yml)

[pentest.yml](https://github.com/snhb2002/Cybersecurity-Project-1/blob/627f88d979a07d19b76e8176478c32b46c8c57f4/ansible/pentest.yml)
  
[filebeat-playbook.yml](https://github.com/snhb2002/Cybersecurity-Project-1/blob/09904737ba8eab3d8883d6d456ecd3b7afe37c0f/ansible/filebeat-playbook.yml)

[metricbeat-playbook.yml](https://github.com/snhb2002/Cybersecurity-Project-1/blob/627f88d979a07d19b76e8176478c32b46c8c57f4/ansible/metric-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology:

The purpose of the network is to present a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing always ensures that the application will be highly available, in addition to restricting access to the network
What is the aspect of security do load balancers protect?
- The aspect of security that load balancers protect is the system from DDoS attacks by shifting traffic. 

What is the advantage of a jump box?
The advantage of a jump box is to give secure access to resources via Private Pre-shared key and SSH. 


Integrating an ELK server allows users to monitor the vulnerable VMs for changes to the system logs and data.
What does Filebeat watch for?
- Filebeat centralizes and forwards log data. Filebeat monitors the locations or log files and collects log events and forwards them either to Logstash for indexing or Elasticsearch.

What does Metricbeat record?
- Metricbeat records the statistics and metrics that it collects and ships them to the output that you specify, such as Logstash or Elasticsearch. With Metricbeat, you can monitor your servers by collecting metrics from the system and services running on the server, such as: Apache.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address    | Operating System |
|----------|----------|---------------|------------------|
| Jump Box | Gateway  | 10.0.0.4      | Linux            |
| ELK      | Gateway  |70.115.247.120 | Linux            |
| Web-1    | LBalancer| FTE-IP        | Linux            |
| Web-2    | LBalancer| FTE-IP        | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet 

Only the Elk machine can accept connections from the Internet. Access to this machine is allowed only from the following IP addresses:
- 70.115.247.120

Machines within the network can be accessed only by Jumpbox via Private-Shared Key & SSH
- Which machine did you allow to access your ELK VM? Jumpbox

What was its IP address?
-52.165.225.245 (Jumpbox Public)
-10.0.0.4 (Jumpbox Private)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 70.115.247.120       |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
What is the main advantage of automating configuration with Ansible?
- Configuration management, single source for application deployment

The playbook implements the following tasks:

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

1.  Check for the presence of docker (Install/Update)
2.  Check for the presence of python3-pip (Install/Update)
3.  Install Docker module
4.  Increase virtual memory
5.  Download and launch docker elk container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance


![Docker-PS](https://github.com/snhb2002/Cybersecurity-Project-1/blob/ed7e939572e7889d8ae9781d9badb1a6c9dd200e/diagrams/docker%20ps.PNG)



### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web-1 10.0.0.5
- Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Webservers

These Beats allow us to collect the following information from each machine:
- Machine health, performance, system logs and events etc.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat file to file-conifg.yml.
- Update the filebeat.yml file to include...
- Run the playbook, and navigateto check that the installation worked as expected  (Screenshot)

![Kibanaserver png](https://github.com/snhb2002/Cybersecurity-Project-1/blob/4f6d312a4650c2e24eff8b8b306af988bb2c78b7/diagrams/updated%20kibana%20screen.PNG)

: Answer the following questions to fill in the blanks:_
- Which file is the playbook? Ansible-playbook files   
- Where do you copy it? Root of ansible 
- Which file do you update to make Ansible run the playbook on a specific machine? hosts configuration file

How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- HostName in Host configuration file

Which URL do you navigate to in order to check that the ELK server is running?
- SSH azureuser@10.0.0.5 (Web-1)
-  http://40.78.4.28:5601/app/#kibana/home

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
![Ansible-Playbook_NAME_OF_PLAYBOOK] 
ssh azureuser@52.165.225.245
sudo docker container list -a
sudo docker start (name)
sudo docker attach (name)
cd /etc/ansibe/
ls
nano metric-playbook.yml



