# CSA Unit 3 — Set Up a Web Application on Amazon EC2

**Cloud Security & Architecture — Problem-Based Learning**
**Student:** Saif Pathan | **Date:** November 2026

---

## Overview

This repository contains the complete Unit 3 submission:
- **Terraform IaC** — provisions EC2, VPC, Security Groups, Nginx bootstrap
- **EC2 Deployment Tool** — full-stack Node.js web UI for the deployment workflow
- **Project Report** — step-by-step documentation with real tool screenshots (PDF)

## Structure

```
CSA-UNIT-3/
├── terraform/               # Terraform IaC — EC2 + networking
│   ├── main.tf              # VPC, Subnet, IGW, Route Table
│   ├── security_groups.tf   # SSH/22 (IP-locked), HTTP/80, HTTPS/443
│   ├── compute.tf           # EC2 t3.micro + Elastic IP + IMDSv2
│   ├── user_data.sh         # Bootstrap: Nginx install + HTML deploy
│   ├── variables.tf
│   └── outputs.tf
├── ec2-tool/                # Working web tool (Node.js/Express)
│   ├── server.js            # REST API backend
│   ├── capture.js           # Puppeteer screenshot script
│   ├── public/index.html    # Brutalist UI frontend
│   └── screenshots/         # 10 real tool screenshots (in PDF)
├── UNIT3_PROJECT_REPORT.pdf # 513KB — report with embedded screenshots
├── UNIT3_PROJECT_REPORT.md  # Markdown source
└── generate_unit3_pdf.py    # PDF generator (ReportLab)
```

## Run the Tool

```bash
cd ec2-tool
npm install
node server.js
# Open http://localhost:4000
```

## Deploy Infrastructure

```bash
cd terraform
ssh-keygen -t rsa -b 4096 -f ~/.ssh/csa-unit3-key
terraform init
terraform apply -var="my_ip_cidr=$(curl -s ifconfig.me)/32"
```

## Related Repositories

- **Unit 1:** https://github.com/saifpathan9969/CSA
- **Unit 2:** https://github.com/saifpathan9969/CSA-UNIT-2-
- **Unit 3:** This repository
