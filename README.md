# Project README

This project encompasses several modules and environments aimed at provisioning infrastructure components for a scalable application deployment.

## Dependencies and Requirements

- Terraform: Version 0.12.0 or higher.
- AWS Provider: Version 3.0.0 or higher.
- Environment: It is recommended to use Windows 10 or Linux operating system. You need to have Terraform installed and configured AWS credentials to access AWS resources.

## Modules

### Networking Module

**Objective:** Create networking resources including public and private subnets.

**Features:**
- Public Subnets: Dynamically created based on specified CIDR blocks.
- Private Subnets: Includes a single NAT gateway, also dynamically configured based on provided CIDR blocks.

**README:** Provides detailed instructions for configuring networking resources and specifying CIDR blocks.

### Autoscaling Module

**Objective:** Implement autoscaling functionalities for application scalability.

**Features:**
- Launch Template: Configurable with default AMI and user-specified AMI.
- Security Groups: Includes dynamic ingress and egress rules attached to the launch template. Additional input variable for supplementary security groups.

**README:** Offers clear guidelines for setting up autoscaling capabilities and defining security group rules.

## Environments

### Dev Environment

**Networking:**
- Utilizes the networking module to create public and private subnets.
- Configured with three CIDR blocks for each subnet type.

**Autoscaling:**
- Utilizes the autoscaling module to deploy an Apache web server with a user data script to private subnets.

**Public module ALB:**
- Implements an Application Load Balancer (ALB) to route incoming traffic to the autoscaling group.

**Outputs:** Upon creation, the CLI should display the DNS name of the ALB for accessing the Apache web page.

### Prod Environment

**Static Website Hosting:**
- Configures an S3 bucket and another resource to host the static website.

**Outputs:** After creation, the CLI should provide the DNS name of the static website for access through a browser.

Each module and environment is designed to facilitate the deployment and management of infrastructure components required for the application's operation and scalability. Refer to individual README files for detailed setup instructions and usage guidelines.

| Command            | Description                                                    |
|--------------------|----------------------------------------------------------------|
| `terraform init`   | Initializes a Terraform working directory.                     |
| `terraform plan`   | Generates and displays an execution plan.                      |
| `terraform apply`  | Applies the changes required to reach the desired state.       |
| `terraform destroy`| Destroys the Terraform-managed infrastructure.                 |
