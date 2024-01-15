[![Board Status](https://dev.azure.com/chukwuemekapeter319/30dbb643-68fb-4aff-9a6b-ad6d1076c860/764cea27-f0e2-44eb-b7c1-937cb9a8eb30/_apis/work/boardbadge/ebc7b16f-60dc-45de-85b3-f6138a3a0dd8)](https://dev.azure.com/chukwuemekapeter319/30dbb643-68fb-4aff-9a6b-ad6d1076c860/_boards/board/t/764cea27-f0e2-44eb-b7c1-937cb9a8eb30/Microsoft.RequirementCategory)

# Minikube commands
Installation: https://minikube.sigs.k8s.io/docs/start/
```
minikube config set driver docker
minikube start // stop
minikube status
minikube dashboard --url
minikube service <applicaiton-service-name>
```

# Kubectl Insallation/Configuration
Installation: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

```
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl


cat ~/.kube/config  // kubectl config view
alias k='kubectl'
```

# Kubectl commands
```
kubectl get namespace
kubectl get deployment
kubectl get replicasetP
kubectl get configmap
kubectl get nodes
kubectl describe nodes
kubectl get events
minikube service mywebapp
```

# Cluster Management
```
kubectl cluster-info
kubectl get nodes
kubectl describe node minikube
kubectl cordon minikube
kubectl drain minikube --ignore-daemonsets=true --force
kubectl uncordon minikube
```

# Namespaces
```
kubectl get namespace
kubectl create namespace dev
kubectl create namespace test
kubectl delete namespace test
k create -f namespaces/namespace-prod.yaml
k describe namespace prod

# OPTIONAL
kubectl config set-context --current --namespace=<NAMESPACE NAME>
```

# Your Hello World Kubernetes Project
```
kubectl get get pods
kubectl get pods -n dev 

kubectl create deployment hello-node --image=k8s.gcr.io/echoserver:1.4
kubectl create deployment hello-node --image=k8s.gcr.io/echoserver:1.4 -n dev
kubectl get deployments --all-namespaces
kubectl get events -n dev
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
kubectl get services
minikube service hello-node
//On cloud providers that support load balancers, an external IP address would be provisioned to access the Service. On minikube, the LoadBalancer type makes the Service accessible through the minikube service command.
```

# Deployments 
```
kubectl apply -f solution/v1.yaml
```

# Service LoadBalancers 
```
kubectl apply -f solution/v2.yaml
```

# Config Maps and Scaling 
```
kubectl apply -f solution/v3.yaml
```

# Resource Limits
```
kubectl apply -f solution/v4.yaml
```



# Troubleshooting, Logs, Rollouts, Draining Nodes 
k describe deployment mydeployment
### Logs
k logs -f -l app=mywebapp
### Rollouts
kubectl rollout 
k rollout restart deployment mydeployment
kubectl drain minikube --ignore-daemonsets=true --force
