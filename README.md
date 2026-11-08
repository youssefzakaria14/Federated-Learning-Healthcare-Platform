# 🏥 FedHealth — Federated Learning Healthcare Platform

<p align="center">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" width="65" height="65" />
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original.svg" width="65" height="65" />
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" width="65" height="65" />
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original-wordmark.svg" width="65" height="65" />
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/fastapi/fastapi-original.svg" width="65" height="65" />
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" width="65" height="65" />
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/ubuntu/ubuntu-original.svg" width="65" height="65" />
</p>
<p align="center">
  **A Secure Healthcare Platform Combining Artificial Intelligence, Federated Learning, and Network Infrastructure.**
</p>

---

## 🧠 About the Project

FedHealth is a healthcare-focused platform designed to support collaboration between multiple hospitals through Federated Learning.

Each participating hospital trains a local machine-learning model using its own dataset. Model updates are exchanged through the federation infrastructure, allowing hospitals to contribute to a shared global model without centralizing their raw training datasets.

The platform integrates backend development, artificial intelligence, database management, network connectivity, VPN security, and server infrastructure.

## 🎯 Project Objectives

- Enable collaborative model training across multiple hospitals.
- Keep raw hospital training datasets within their local environments.
- Provide AI-powered healthcare predictions.
- Manage users, hospitals, predictions, and dashboard information.
- Establish secure communication between distributed servers.
- Protect sensitive application data.
- Monitor hospital participation and federated training activities.

## ✨ Core Features

| Feature | Description |
|---|---|
| 🔐 Authentication | JWT-based authentication and protected APIs |
| 👥 Role-Based Access | Doctor and Administrator permissions |
| 🏥 Hospital Management | Hospital records and participant management |
| 🤖 AI Integration | Python-based prediction service |
| 🧠 Federated Learning | Local training and collaborative model updates |
| 📊 Dashboard | Hospital and model-training information |
| 🔒 Data Encryption | Encryption for selected sensitive fields |
| 🌐 Private Networking | Server connectivity through WireGuard VPN |
| 🧱 Network Security | Firewall policies and controlled traffic |
| 📚 API Documentation | Interactive Swagger UI |

## 🏗️ Overall System Architecture

```text
                    FEDHEALTH PLATFORM
                            |
       +--------------------+--------------------+
       |                    |                    |
    BACKEND              AI-PILOT           INFRASTRUCTURE
       |                    |                    |
  Node.js / Express     Python / FastAPI     Central Server
      MongoDB             ML Models          Client Server
       |                    |               Hospital Servers
       +--------------------+--------------------+
                            |
                      NETWORK LAYER
                            |
                     WireGuard VPN
                     Firewall Rules
                     Private Routing
```

## 🧠 Federated Learning Architecture

The federated learning architecture enables hospitals to train local models and exchange model updates through the infrastructure layer.

```text
+----------------------+       +----------------------+
|     Hospital 1       |       |     Hospital 2       |
|                      |       |                      |
| Local Dataset        |       | Local Dataset        |
| Local Training       |       | Local Training       |
+----------+-----------+       +----------+-----------+
           |                              |
           +--------------+---------------+
                          |
                   WireGuard VPN
                          |
                  +-------v-------+
                  | Client Server |
                  | Update Relay  |
                  +-------+-------+
                          |
                   WireGuard VPN
                          |
                  +-------v-------+
                  | Central Server|
                  | Model         |
                  | Aggregation   |
                  +-------+-------+
                          |
                     Global Model
                          |
                  Client Server Relay
                          |
               +----------+----------+
               |                     |
           Hospital 1            Hospital 2
```

**Federated Learning Workflow:**

1. Each hospital trains a local model using its own dataset.
2. Hospital servers send model updates to the Client Server.
3. The Client Server forwards updates to the Central Server.
4. The Central Server coordinates model aggregation.
5. The resulting global model is returned through the Client Server.
6. The Client Server distributes the global model to participating hospitals.

The intended architecture routes hospital updates through the Client Server instead of direct hospital-to-central communication.

## 🌐 Network Infrastructure

The infrastructure uses a distributed server architecture connecting hospital environments with client and central servers.

### Network Components

| Component | Responsibility |
|---|---|
| Central Server | Coordinates federated learning and global model management |
| Client Server | Relays communication between hospitals and central infrastructure |
| Hospital Server 1 | Performs local training and sends model updates |
| Hospital Server 2 | Performs local training and sends model updates |
| WireGuard VPN | Provides encrypted network connectivity |
| Firewall | Controls allowed incoming and outgoing traffic |

### Network Topology and IP Addressing

The following table represents the proposed lab network addressing plan:

| Machine | LAN IP Address | WireGuard VPN IP |
|---|---|---|
| Central Server | `192.168.50.1` | `10.8.0.1` |
| Client Server | `192.168.50.2` | `10.8.0.2` |
| Hospital Server 1 | `192.168.50.11` | `10.8.0.3` |
| Hospital Server 2 | `192.168.50.12` | `10.8.0.4` |

**Network Configuration:**

- VPN Network: `10.8.0.0/24`
- LAN Network: `192.168.50.0/24`
- VPN Technology: WireGuard
- Server Environment: Linux / Ubuntu
- Virtualization: Oracle VirtualBox

> Note: The IP addresses above are a proposed documentation addressing plan. They must be verified against the actual WireGuard configurations, routes, and VirtualBox network settings before deployment.

### 🔐 WireGuard VPN

WireGuard is used to establish encrypted communication channels between authorized infrastructure nodes.

**Main Responsibilities:**

- Establish secure VPN tunnels.
- Provide private IP addressing.
- Protect communication between connected servers.
- Support controlled server-to-server routing.
- Reduce exposure of internal services to public networks.
- Allow authorized infrastructure nodes to communicate securely.

### 🧱 Firewall and Network Security

Firewall policies help control network access and protect internal services.

The security approach includes:

- Allowing only required service ports.
- Restricting unauthorized incoming connections.
- Limiting administrative access to trusted machines.
- Allowing VPN communication only between authorized peers.
- Protecting internal APIs and model-transfer services.
- Keeping VPN private keys and credentials outside source control.

Actual firewall rules and service ports must match the deployed server configurations.

### Network Communication Flow

1. Hospital servers perform local model training.
2. Hospitals send their model updates to the Client Server.
3. The Client Server forwards updates to the Central Server.
4. The Central Server performs the configured aggregation process.
5. The global model is returned to the Client Server.
6. The Client Server distributes the updated model to hospital participants.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | Backend Runtime |
| Express.js | REST API Framework |
| MongoDB Atlas | Cloud Database |
| Mongoose | Database Modeling |
| JWT | Authentication |
| bcryptjs | Password Hashing |
| Python | AI Development |
| FastAPI | AI Service API |
| Scikit-learn | Machine Learning |
| WireGuard | VPN Connectivity |
| Linux / Ubuntu | Server Operating System |
| VirtualBox | Virtual Server Environment |
| Firewall | Network Traffic Control |
| Swagger | API Documentation |
| AES-256-GCM | Selected Field Encryption |
| Git & GitHub | Version Control |

## 📂 Project Structure

```text
Fedrated-Learning-pilot/
│
├── Controllers/
├── Middleware/
├── Model/
├── Routes/
├── Utils/
│
├── AI-Pilot/
│   ├── 1_prepare_data.py
│   ├── 2_train_federated.py
│   ├── 3_app.py
│   ├── 4_api.py
│   ├── datasets/
│   └── model artifacts
│
├── Infrastructure/
│   ├── Central-Server/
│   ├── Client-Server/
│   ├── Hospital-Server-1/
│   └── Hospital-Server-2/
│
├── Documentation/
│
├── app.js
├── swagger.js
├── package.json
├── .gitignore
└── README.md
```

## ⚙️ Getting Started

### Prerequisites

- Node.js and npm
- MongoDB database
- Python and pip
- Git
- Linux / Ubuntu for server infrastructure
- VirtualBox for the virtual-machine lab

### 1. Clone the Repository

```bash
git clone https://github.com/youssefzakaria14/Fedrated-Learning-pilot.git

cd Fedrated-Learning-pilot
```

### 2. Install Backend Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a local `.env` file using the exact environment variable names required by the backend configuration.

Typical configuration includes:

- Backend port
- MongoDB connection string
- JWT secret
- AI service URL
- Encryption key

Never upload real credentials, API keys, database connection strings, or encryption keys to GitHub.

### 4. Start the Backend

```bash
npm start
```

### 5. Run the AI Service

Create a separate Python environment, install the dependencies listed in the AI-Pilot requirements file, and run the AI service using its configured entry point.

### 6. Open Swagger Documentation

```text
http://localhost:3000/api-docs
```

Replace the port if the backend uses a different configuration.

## 📡 Backend API Modules

| Module | Purpose |
|---|---|
| Authentication | User registration and login |
| Hospitals | Hospital and participant management |
| Predictions | AI prediction requests and results |
| Dashboard | Hospital and training information |
| Swagger | Interactive API documentation |

For exact HTTP methods, request bodies, response formats, and authorization requirements, refer to the current route definitions and Swagger configuration.

## 🔒 Security

- JWT authentication for protected API endpoints.
- Role-based authorization for doctors and administrators.
- Password hashing before storage.
- Encryption of selected sensitive database fields.
- Environment variables for credentials and secrets.
- WireGuard encrypted tunnels for private infrastructure communication.
- Firewall policies to restrict unnecessary network access.
- No private keys or real credentials in source control.

Encryption and VPN connectivity are security layers; they do not replace secure key management, authorization, auditing, or HTTPS/TLS where required.

## 📚 Documentation

Detailed technical documentation is available in the `Documentation/` directory.

It covers:

- Project Overview.
- System Architecture.
- Backend Installation.
- API Documentation.
- Network Architecture.
- VPN and Infrastructure Configuration.

## 🚀 Future Improvements

- Complete and validate all server deployment configurations.
- Add more hospital participants.
- Automate infrastructure deployment.
- Expand centralized monitoring and logging.
- Add automated testing and CI/CD.
- Improve audit logging and infrastructure monitoring.

---

<p align="center">
  **FedHealth — Healthcare • Artificial Intelligence • Federated Learning • Network Security**
  <br>
  <sub>Node.js · Express.js · MongoDB · Python · FastAPI · Linux · WireGuard · VirtualBox</sub>
</p>
