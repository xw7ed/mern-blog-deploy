# 🚀 MERN Stack Blog App Deployment - Week 11 Assignment

This project demonstrates the full deployment of a **MERN stack blog application** using **Terraform**, **Ansible**, and **AWS infrastructure**. The deployment includes automatic provisioning of backend and frontend, MongoDB Atlas setup, and secure media upload through S3.

---
## 🖼️ Infrastructure Diagram

![Architecture Diagram](./images/diagram.png)

---

## 📐 Architecture Overview

```
                   +---------------------+
                   |   MongoDB Atlas     |
                   |  (Cloud Database)   |
                   +----------^----------+
                              |
                       +------|------+
                       |   EC2 (API)  |
                       |  Ubuntu 22.04|
                       +------+-------+
                              |
         +--------------------+--------------------+
         |                                         |
 +-------+--------+                      +---------+--------+
 |  S3 Media Bucket |                    |  S3 Frontend     |
 | (Private access) |                    | (Static hosting) |
 +------------------+                    +------------------+
```

---

## ⚙️ Components Used

- **Terraform**: Infrastructure provisioning (EC2, IAM, S3)
- **Ansible**: Backend & frontend provisioning
- **MongoDB Atlas**: Cloud NoSQL database
- **AWS EC2**: Host backend
- **AWS S3**: Host frontend & media storage

---

## 🛠 Deployment Steps

### 1️⃣ Terraform Setup

```bash
terraform init
terraform apply
```

- Provisions IAM user for media access
- Configures EC2 instance and security groups
- Sets up S3 buckets (frontend & media)

### 2️⃣ MongoDB Atlas

- Create free-tier cluster
- Whitelist EC2 IP
- Create DB user and get connection string
- Update Ansible `vars/main.yml` with URI

### 3️⃣ Ansible Backend

```bash
ansible-playbook -i inventory backend-playbook.yml
```

- Clones project repo
- Configures `.env` file
- Installs dependencies
- Starts app with PM2

### 4️⃣ Ansible Frontend

```bash
ansible-playbook -i inventory frontend-playbook.yml
```

- Generates frontend `.env`
- Builds project using pnpm
- Deploys to S3 static website

---

## ✅ Success Criteria

- Backend runs on EC2 & connected to MongoDB Atlas
- Media upload to S3 via IAM
- Frontend loads from S3
- `.env` is configured correctly

---

## 📸 Screenshots (in `/images` folder)
- `diagram.png`
- `pm2-backend-running.png`
- `mongodb-cluster.png`
- `media-upload-success.png`
- `s3-frontend-working.png`
- `EC2-blog-backend-Running.png`
- `Terraform-created successfully.png`
- `ansible-playbook -i inventory backend-playbook.yml.png`
- `ansible-playbook -i inventory frontend-playbook.yml.png`
---

Author
---
Abdulwahed Alhomaidani
---
Week 11 Assignment – Cloud Deployment
📌 Final Notes

    Project demonstrates real-world IaC (Infrastructure as Code) with Terraform + Ansible.

    All components are modular and reusable.


