# aws_lambda_hackathon
# 🔐 SecureLink: One-Time Encrypted Link Generator

A serverless Python-based application that allows users to generate encrypted, one-time-use links to securely share confidential messages. Powered by *AWS Lambda* and *API Gateway*, SecureLink ensures privacy, encryption, and auto-destruction of sensitive content after first access.

---

## 🚀 Features

- One-time access: Each link can only be used once.
- AES-256 encryption using cryptography.fernet.
- Unique URLs via UUID tokens.
- Fully serverless and scalable using AWS Lambda.
- Easy integration with frontend or API clients.

---

## 🛠 AWS Services Used

| AWS Service        | Purpose                                      |
|--------------------|----------------------------------------------|
| *AWS Lambda*     | Executes encryption, link generation, and self-destruction logic |
| *Amazon API Gateway* | Exposes HTTP endpoints to interact with Lambda |
| *AWS CloudWatch* | Logs all requests and errors for monitoring |
| *AWS IAM*        | Provides access control and execution permissions |

---

## 🧠 How AWS Lambda is Used

AWS Lambda is the backend compute engine for this app. It:
- Accepts a POST request to /generate with a secret message.
- Encrypts the message using AES (Fernet) and generates a unique UUID.
- Stores the encrypted message temporarily in a dictionary (or DB).
- Generates a one-time-use URL tied to the UUID.
- When accessed via GET /access/{uuid}, it decrypts the message once, deletes it, and blocks further access.

This architecture allows complete stateless, serverless, scalable deployment without managing any infrastructure.

---

[ Clone the repository:https://github.com/GUNDESANDEEP/AWS-Lambda-inOne-Time-Encrypted-Link-Generator/tree/main](https://github.com/GUNDESANDEEP/AWS-Lambda-inOne-Time-Encrypted-Link-Generator/tree/main )

## 📌 API Endpoints

### POST /generate
*Description:* Generate a one-time secure link.

*Request Body:*
```json
{
  "message": "Your secret message"
}


