# saas-nginx-manifests
We are building a cloud-native SaaS prototype that automates the deployment of AI-powered applications using a GitOps workflow. The core of the project is a Kubernetes cluster hosted on AWS EC2, which provides a scalable environment for our services. To eliminate manual work, we’ve integrated ArgoCD, an automation engine that monitors our GitHub repository; whenever we push a change to our configuration files, the cluster automatically updates itself within three minutes to reflect those changes
This YAML manifest serves as the blueprint for our automated infrastructure. By defining our environment as code, we ensure that the deployment remains predictable and self-healing.

# 1. The Deployment (saas-nginx-server)
High Availability: Configured with 3 replicas to ensure service redundancy across the cluster.

Self-Healing: Kubernetes continuously monitors these pods; if an instance fails, the cluster automatically replaces it to maintain the desired state.

Resource Management: Uses the official Nginx image as a standardized web-server layer to handle incoming traffic.

# 2. The Service (nginx-service)
Stable Networking: Provides a permanent internal entry point for the application, abstracting the dynamic IP addresses of individual pods.

Load Balancing: Automatically distributes incoming TCP traffic on Port 80 across all healthy replicas using label selectors.

Decoupling: Allows external traffic to reach our deployment without needing manual updates to networking rules whenever pods are scaled or restarted.
