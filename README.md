referred blog : https://contabo.com/blog/kubernetes-helm/

### create the chart:

```
helm create nginx-chart
```
### Deploy the Chart

```
helm install my-nginx nginx-chart
``` 

Here’s a detailed and concise README for your Helm learning repo, covering the basics of Helm, your example project, and other key aspects.

---

# Learning Helm

Welcome to the **Learning Helm** repository! This repository contains a sample project to understand the basics of Helm, including how to create and manage Helm charts for Kubernetes applications. Here we deploy an NGINX web server using a custom Helm chart.

## What is Helm?

**Helm** is a package manager for Kubernetes, making it easier to define, install, and manage Kubernetes applications.

### Key Features of Helm:
- **Charts**: Helm packages are called charts. Charts contain all the resource definitions needed to run an application in Kubernetes.
- **Templating**: Helm uses Go templates to dynamically configure resources.
- **Versioning**: Helm allows versioning of charts and easy upgrades or rollbacks to previous versions.
- **Dependency Management**: Charts can depend on other charts, which Helm manages.
- **Reusability**: Charts can be shared and reused for different Kubernetes applications.

## Basic Helm Commands

Here are some fundamental commands to get started with Helm:

- **Install a Chart**:
  ```bash
  helm install <release-name> <chart-name>
  ```
- **Upgrade a Chart**:
  ```bash
  helm upgrade <release-name> <chart-name>
  ```
- **Uninstall a Chart**:
  ```bash
  helm uninstall <release-name>
  ```
- **List Releases**:
  ```bash
  helm list
  ```

## Project Structure

This repository contains a Helm chart to deploy an NGINX web server on Kubernetes using Minikube. Here's the structure of the repository:

```
learn-helm/
│
├── nginx-chart/              # The Helm chart for deploying NGINX
│   ├── Chart.yaml            # Chart metadata
│   ├── values.yaml           # Default configuration values
│   └── templates/            # Kubernetes manifests for resources
│       ├── deployment.yaml   # NGINX deployment configuration
│       ├── service.yaml      # NGINX service (NodePort) configuration
│
└── README.md                 # This file
```

### Chart Explanation

- **Chart.yaml**: Contains metadata like name, version, and description of the chart.
- **values.yaml**: Configurable values such as the image repository, tag, and replica count.
- **deployment.yaml**: Defines a Kubernetes deployment for NGINX using the specified image and replica count.
- **service.yaml**: Exposes the NGINX deployment as a service using NodePort, making it accessible outside the cluster.

## How to Use the Chart

1. **Prerequisites**:
   - Kubernetes cluster (e.g., Minikube)
   - Helm installed on your system

2. **Clone this Repository**:
   ```bash
   git clone https://github.com/<your-username>/learn-helm.git
   cd learn-helm
   ```

3. **Create and Deploy the Helm Chart**:
   - Install the chart:
     ```bash
     helm install my-nginx nginx-chart/
     ```

4. **Access the NGINX Application**:
   - After deploying the Helm chart, forward the port to your local machine:
     ```bash
     kubectl port-forward service/my-nginx-nginx-chart 8080:80
     ```
   - Access the NGINX website in your browser at `http://localhost:8080`.

Alternatively, if using NodePort:
   - Get the Minikube IP and NodePort:
     ```bash
     minikube ip
     kubectl get services
     ```
   - Visit the NGINX site using `http://<minikube-ip>:<node-port>`.

## Learn More

Here are some useful links to dive deeper into Helm:
- [Helm Documentation](https://helm.sh/docs/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Helm Chart Best Practices](https://helm.sh/docs/chart_best_practices/)

---

Feel free to adjust the structure or the content as needed for your specific project or learning journey.
