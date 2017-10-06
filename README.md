# Prérequis
dnsmasq https://gist.github.com/davebarnwell/c408533d608bfe24f4f5

Minikube https://kubernetes.io/docs/tasks/tools/install-minikube/#install-minikube


# Installation http service
```shell
kubectl create -f http-svc.yaml
```

## Passage temporaire en loadbalancer
```shell
> kubectl patch svc http-svc -p '{"spec":{"type": "LoadBalancer"}}'
> kubectl get svc http-svc
```
Ouvrir le lien pour visualiser le résultat

http://192.168.99.100:30301

## Retour en nodeport
``` 
kubectl patch svc http-svc -p '{"spec":{"type": "NodePort"}}'
``` 

# Installation de traefik
```
kubectl create -f traefik.yaml
``` 
Ouvrir le lien pour visualiser traefik http://traefik-ui.dev

# Installer ingress pour le service http
```
kubectl create -f http-ing.yaml
```
Ouvrir le lien pour vérifier  http://http-svc.dev/

# Scale http 
``` 
kubectl scale --replicas=3 deployments/http-svc
```

# Exemple de path
```
kubectl create -f http-ing.2.yaml
```
Ouvrir le lien pour vérifier  http://http-svc2.dev/http

        




