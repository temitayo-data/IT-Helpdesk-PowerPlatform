
# 🛠️ IT Helpdesk Automated Ticketing System

## 📌 Project Overview
The **IT Helpdesk Automated Ticketing System** is a model-driven application built on Microsoft Power Platform. It streamlines how employees submit IT requests and how IT agents manage, resolve, and track those issues.

The system automates the entire ticket lifecycle from submission alerts and status updates to resolution emails and ticket archiving while maintaining strict data security so users can only access their own submitted requests.

---

## 🏗️ System Architecture & Tools
* **Power Apps (Model-Driven App):** Provides the user interface for submitting, viewing, and managing support tickets.
* **Microsoft Dataverse:** Serves as the central backend database storing all ticket details, user roles, and system statuses.
* **Power Automate:** Drives the automated background workflows for emails, notifications, and record archiving.
* **Exchange Online / Outlook:** Delivers automated email alerts to employees and IT managers.

---

## ✨ Key Features & Capabilities

### 1. Unified Request Portal
* Custom form capturing essential request details: **Ticket Title**, **Category**, **Priority**, and **Description**.
* Clean layout designed to simplify ticket submission for standard employees.

### 2. Role-Based Access & Security
* **Data Isolation:** Employees can only see tickets they personally created.
* **Read-Only Post-Submission:** Once a ticket is submitted, the form automatically locks into read-only mode for the employee to prevent unauthorized edits.
* **Custom Security Role (`IT Helpdesk - Employee`):** Configured to allow ticket creation and viewing while restricting table edit privileges.

### 3. Dynamic Field Control
* **Resolution Notes Visibility:** The `Resolution Notes` field remains hidden when a new ticket is being created by an employee.
* **IT Agent Access:** The `Resolution Notes` field dynamically reveals itself when an IT agent opens the ticket to work on or resolve the issue.

### 4. End-to-End Automation (Power Automate)
* **IT Alert Flow:** Sends an instant email notification to the IT Manager whenever a new ticket is submitted.
* **Employee Confirmation Flow:** Automatically emails the employee confirming their ticket was successfully received.
* **Resolution Notification Flow:** Automatically triggers when an IT agent changes a ticket status to **Resolved**, emailing the user with the final **Resolution Notes**.
* **Automatic Lifecycle Archiving:** Updates resolved records to an **Inactive** state in Dataverse, cleanly moving them from active views into the **Inactive Tickets** archive.

Email Notifications
<img width="1920" height="1080" alt="Screenshot (200)" src="https://github.com/user-attachments/assets/dd6b6576-f8d9-47d4-918d-48c0431d4140" />

<img width="1920" height="1080" alt="Screenshot (201)" src="https://github.com/user-attachments/assets/d52c12d0-adff-4c34-9d99-3cfd8f683678" />

<img width="1920" height="1080" alt="Screenshot (202)" src="https://github.com/user-attachments/assets/d380887c-f412-4dd1-8f1d-9f3f9e7093bd" />

New Ticket Page
<img width="1920" height="1080" alt="Screenshot (203)" src="https://github.com/user-attachments/assets/508d0340-e5d7-4a11-8938-6c03aae3fb0d" />

Detailed Report
<img width="1920" height="1080" alt="Screenshot (204)" src="https://github.com/user-attachments/assets/06bc38b5-a990-45b0-bd3a-f73b5d0eb4bb" />

Power Automate Flows
<img width="1920" height="1080" alt="Screenshot (205)" src="https://github.com/user-attachments/assets/df8a3e2e-5167-4ef8-b77d-31c6c3c4ebf2" />

<img width="1920" height="1080" alt="Screenshot (206)" src="https://github.com/user-attachments/assets/bba6fd9c-cb73-4fae-9c2a-ce71472cece0" />

##🔒 Security & Data Governance Summary
##Security Layer         Configuration Details
##Role Assignment        Restricted to IT Helpdesk - Employee role (conflicting default roles like Basic User removed).
##Table Permissions      Create (User level), Read (User level), Write (None), Delete (None).
##Form Access            Read-Only view enforced across submitted records for regular employees.
---

## 🔄 Ticket Lifecycle Workflow

```text
[ Employee Submits Ticket ]
            │
            ├──► Power Automate sends confirmation email to Employee
            ├──► Power Automate sends alert email to IT Manager
            │
[ IT Agent Reviews Ticket ]
            │
            ├──► Ticket Status updated (e.g., "In Progress")
            ├──► Resolution Notes field becomes visible to IT Agent
            │
[ IT Agent Resolves Ticket ]
            │
            ├──► Status changed to "Resolved" & Resolution Notes added
            ├──► Power Automate emails Employee with Resolution Notes
            └──► Flow deactivates ticket ➔ Moves to "Inactive Tickets" View

