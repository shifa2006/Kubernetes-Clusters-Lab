# Kubernetes-Clusters-Lab
Kubernetes cluster setup using kind, Docker Desktop, and NGINX
# Kubernetes Lab on Windows

## 1. Objective
To create a local Kubernetes cluster on Windows using WSL2, Docker Desktop, kubectl, and kind. Deploy NGINX, scale the deployment, and test the self-healing feature of Kubernetes.

## 2. Tools and Technologies
- Windows
- WSL2 (Ubuntu)
- Docker Desktop
- Kubernetes
- kubectl
- kind
- NGINX

## 3. Cluster Configuration
The Kubernetes cluster consists of:
- 1 Control Plane Node
- 2 Worker Nodes

The cluster configuration is available in [`kind-config.yaml`](kind-config.yaml).

## 4. Cluster Setup
The cluster was created using the following command:

```bash
kind create cluster --config kind-config.yaml
```

The cluster was created successfully.

## 5. Verify Kubernetes Nodes

```bash
kubectl get nodes
```

All three nodes were successfully created and reached the `Ready` status.

## 6. Deploy NGINX

```bash
kubectl create deployment web --image=nginx --replicas=3
```

An NGINX deployment was created with three replicas.

## 7. Scale the Deployment

```bash
kubectl scale deployment web --replicas=6
```

The deployment was scaled from three replicas to six replicas.

The Pods were verified using:

```bash
kubectl get pods
```

All six Pods reached the `Running` status.

## 8. Test Kubernetes Self-Healing

One Pod was deleted using:

```bash
kubectl delete pod web-64c966cf88-7tphc
```

Kubernetes automatically created a replacement Pod to maintain the desired number of replicas.

The final verification showed six Pods in the `Running` status.

## 9. Screenshots

They include:
- Docker Hello World
- kubectl and kind versions
- Cluster creation
- Kubernetes nodes
- NGINX scaling
- Pod self-healing
- Cluster configuration

## 10. Conclusion
A local Kubernetes cluster was successfully created using kind on Windows. NGINX was deployed and scaled from three to six replicas. The self-healing feature was verified by deleting a Pod and observing the automatic creation of a replacement Pod.

