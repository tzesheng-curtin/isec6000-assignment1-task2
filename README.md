<div align="center">
  <h1>ISEC 6000
  <div>Assignment 1 - Task 2</div>
  <div>Setup Saleor Platform on Linux Virtual Machines (VM)</div>
  </h1>
</div>
This document outlines the steps required to setup the Saleor Platform on a Linux Virtual Machine using docker compose. The following service are included in Saleor Platform:

1. Core GraphQL API
2. Dashboard
3. Storefront
4. Checkout App
5. Mailpit
6. Jaeger
7. The essential databases, cache, workers, etc.


## Requirements
1. Linux VM with Superuser access
2. [Git](https://github.com/git-guides/install-git) installed on VM
3. [Docker](https://docs.docker.com/install/) installed on VM

## Setting up Saleor Platform in Virtual Machines
### 1. Run the following command to clone the repository:
```
git clone https://github.com/tzesheng-curtin/isec6000-assignment1-task2.git
```

### 2. Navigate to the cloned directory:
```shell
cd isec6000-assignment1-task2
```

### 3. Build the application:
```shell
docker compose build
```

### 4. Apply Django migrations:
```shell
docker compose run --rm api python3 manage.py migrate
```

### 5. Populate the database with example data and create the admin user:
```shell
docker compose run --rm api python3 manage.py populatedb --createsuperuser
```
*Note that `--createsuperuser` argument creates an admin account with the following credentials:*
>Username : `admin@example.com`\
Password :`admin`

### 6. Run the application:
```shell
docker compose up -d
```

## Accessing Saleor Applications
Once the application is running successfully, the Saleor Applications can be accessed through the following links:
- Saleor Core (API) - http://localhost:8000
- Saleor Dashboard - http://localhost:9003
- Saleor Storefront - http://localhost:3009
- Saleor Checkout App - http://localhost:3001
- Jaeger UI (APM) - http://localhost:16686
- Mailpit (Test email interface) - http://localhost:8025
