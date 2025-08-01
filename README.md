# 📘 README: Flask + NGINX Load Balancer with Docker

This project demonstrates a simple load balancing setup using **Flask**, **NGINX**, and **Docker Compose**. Useful for local development and understanding how to distribute traffic across multiple app instances.

---

## 📦 Features

- Load balancing using NGINX upstream
- Rate limiting using NGINX `limit_req`
- Health checks for Flask apps
- Dockerized environment

---

## 📁 Project Structure

```
flask-nginx-lb/
├── app/
│   ├── app.py
│   └── Dockerfile
├── nginx/
│   └── default.conf
├── docker-compose.yml
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone and Navigate

```bash
git clone https://github.com/rifqiaz06/flask-nginx-lb.git
cd flask-nginx-lb
```

### 2. Run Docker Compose

```bash
docker-compose up --build
```

### 3. Access the App

Open in browser:

```
http://localhost:8080
```

Refresh the page a few times to see load balancing between different containers.

---

## 🔍 Health Check

Each Flask instance exposes a health endpoint at `/health`. NGINX also exposes a health check at `/health` directly via the load balancer.

---

## 🛠️ Configuration Overview

### Flask App: `app/app.py`

- Simple web server that returns hostname
- Health check route at `/health`

### Dockerfile: `app/Dockerfile`

- Based on Python slim
- Installs Flask and runs the app

### NGINX Config: `nginx/default.conf`

- Defines upstream with 3 Flask containers
- Adds basic rate limiting
- Forwards traffic to `/` and `/health`

### Compose File: `docker-compose.yml`

- Spins up 3 Flask containers
- Configures NGINX as reverse proxy & load balancer
- Exposes app at port 8080

---

## 🌈 Optional Enhancements

- Add HTTPS with certbot (for production)
- Add logging for NGINX access/error
- Implement custom error pages
- Integrate Prometheus & Grafana for monitoring

---

## 📚 References

- Flask: [https://flask.palletsprojects.com/](https://flask.palletsprojects.com/)
- NGINX: [https://nginx.org/en/docs/](https://nginx.org/en/docs/)
- Docker Compose: [https://docs.docker.com/compose/](https://docs.docker.com/compose/)
- NGINX Rate Limiting: [https://nginx.org/en/docs/http/ngx_http_limit_req_module.html](https://nginx.org/en/docs/http/ngx_http_limit_req_module.html)

---
