In this project we deploy microservices application (online shop) on linode's k8s cluster




create linode k8s cluster

save kubeconfig file online-shop-ms-demo-linode-kubeconfig.yaml
chmod 600 online-shop-ms-demo-linode-kubeconfig.yaml
export KUBECONFIG=online-shop-ms-demo-linode-kubeconfig.yaml

check:
kubectl get nodes


kubectl create ns microservices
kubectl apply -f k8s-deployment.yaml -n microservices
kubectl get pods -n microservices
kubectl get svc -n microservices

check the application in browser


Another option is to deploy microservices application using helm charts, you can use helmfile to manage all helm charts in one file.
We can use reusable configuration files
What we already did:
  helm create microservice //
  helm template -f email-service-values.yaml microservice // to preview filled template
  helm lint -f email-service-values.yaml microservice // check correctness of yaml file
  helm ls
  helm install --dry-run=client -f values/redis-values.yaml rediscart charts/redis
  helm install -f values/redis-values.yaml rediscart charts/redis
helmfile sync // to apply all helm charts in helmfile.yaml, you need to install helmfile command first
helmfile destroy // to delete all helm charts in helmfile.yaml











