# Overview
- Overview and quick understanding of what DevOps is as a philosophy
- Covers a quick overview of CI/CD, Monitoring, Security
- History of traditional development -> QA -> Security -> Operation code integration and deployment methology so that we understand what problems we are looking to solve with philosophy of DevOps

# Readings
- [What is devops](https://aws.amazon.com/devops/what-is-devops/)
- [How did devops come to be](https://cloud.google.com/blog/products/gcp/sre-vs-devops-competing-standards-or-close-friends)
- [Philosophy of devops](https://itrevolution.com/devops-culture-part-1/)
- [Infrastructure as Code(IAC)](https://searchitoperations.techtarget.com/definition/Infrastructure-as-Code-IAC)
- [The Linux Directory Structure, Explained](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/)
- [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/pub/fhs-2.3.html)
- [systemd](https://wiki.archlinux.org/index.php/systemd)

# Basics
- Operation System (Linux)
- unix file system
- Scripting (bash)
- Programming (ruby, python, java...etc, as long as you are okay one of the modern programming language)

# Get started
- Sign up for AWS
- Spin up a Ubuntu Server VM
- Learn about how Linux file system (/sys /usr /var)
- Learn about service management on Linux (systemd)
- Install a basic web service

## Steps

### Create an AWS EC2 instance
1. Head over to [AWS](https://aws.amazon.com/console/) and sign up a new account. This will include 12 months of free tier access. 
2. After you have signed up and logged in. You should be on the [AWS Management Console]() page. Look for **EC2** under **Compute** or just head over to [EC2](https://us-west-2.console.aws.amazon.com/ec2/v2/home?region=us-west-2#Home)
    - If you have time, here is a [AWS Overview](https://docs.aws.amazon.com/aws-technical-content/latest/aws-overview/aws-overview.pdf), **Read page 1-8, 18-22, 22-25, 50-53. The topics you will be focusing on are Compute, Database, and Networking. This includes understanding terminology such as Virtual Machines, VPC, Elastic Load Balancer, RDS Database.**
<!-- 3. To Launch an EC2 (VM) instance, from the link of step 2, Click *Launch Instance*
    1. Select *Ubuntu Server 18.04 LTS (HVM), SSD Volume Type (64-bit x86)* 
    2. Select *General Purpose - t2 micro type*, then click *Next: Configure Instance Details* 
    3. Under Network and Subnet sections, Click *Create new VPC* and *Create new Subnet* 
        - If you want to read more about VPC and Subnet on AWS, head over to [AWS Overview](https://docs.aws.amazon.com/aws-technical-content/latest/aws-overview/aws-overview.pdf) and read page 50 for the overview or read up [What is Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) 
    4. Once you have completed the steps above...  -->
3. Follow Step 1 and Step 2 from [AWS Quick Start Guide: Launch a Linux Virtual Machine](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/welcome.html), Once you completed that, you should be logged into the terminal of the launched EC2 instance.

- In addition, watch a simple [AWS Training Video](https://www.youtube.com/watch?v=zkzED9HvMG0). The video diverts the topic into Machine Learning around half way point. Stop at that point. 

### Filesystem Hierarchy
- In unix systems, every configuration is stored or being modified as a file. To have a better grasp of where those file could be, head over to [The Linux Directory Structure, Explained](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/). Make sure you at least know **var, etc, usr, bin, and dev.**

### What is systemd
- Read [systemd](https://wiki.archlinux.org/index.php/systemd) through section 1. 

### What did we do
```
       VPC                   AWS EC2
     +-----+   +-------------------------------------------+
     |     |   |                                           |
     |     |   |                                           |
     |     |   |          +-------------------+            |
     |     |   |          |      Virtual      |            |
     |     |   |    Network      Machine      |            |
<------------------>Interface                 |            |
     |     |   |       +--+                   |            |
     |     |   |          |                   |            |
     |     |   |          |                   |            |
     |     |   |          +----+---------+----+            |
     |     |   |               ^         ^                 |
     |     |   |               |         |                 +
     |     |   |               |   Resources: CPU, RAM, Storage
     |     |   |               |         |                 |
     |     |   |               |         |                 |
     +-----+   +-------------------------------------------+
               +-------------------------------------------+
               |          |          |          |          |
               | Physical | Physical | Physical | Physical |
               | Machine  | Machine  | Machine  | Machine  |
               |          |          |          |          |
               |          |          |          |          |
               +----------+----------+----------+----------+
```

### Create a simple web service on the EC2 instance
1. From the AWS EC2 Console, select "Instances" from the left pane. Click on the instance you have just created
2. From the bottom pane, details about this EC2 instance should show up. Look for "Security groups", you should see "[Security Group Name]", "view inbound rules", "view outbound rules". Select "[Security Group Name]"
3. This should navigate you to the security groups page, with the security group you have selected earlier targeted. At the bottom pane, click on "Inbound"
4. Selected "Edit"
5. Click on "Add Rule", Select Type "HTTP"
6. Click Save. 
7. From the steps of [Connect to your Amazon EC2 Instance](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-2-connect-to-instance.html), SSH to the VM we have created earlier. 
8. Execute the following commands to install Nginx, a webserver. To read more about Nginx please continue at [about nginx](http://nginx.org/en/)
    ```bash
    sudo amazon-linux-extras install nginx1.12 -y
    sudo systemctl enable nginx
    sudo systemctl start nginx
    ```
9. You should now be able to navigate from your internet browser to http://"[Instance IP address]" and see a successfull running web server. 

# Goals
Good understanding of:
- Virtual Machine (EC2)
- Container (Docker)
- Networking (VPC and Subnets)
- Operation Systems (Linux)
- IAS v.s PAS v.s SAS
