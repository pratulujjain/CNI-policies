Prereqs:
1) We have added "busybox" namespace to the Globaldefault deny policy. This means that all the ingress traffic to the busybox namespace will not be denied whereas all the ingress traffic to the nginx namespace will be denied.

**# kubectl apply -f nginx.yaml -n nginx
**# kubeactl apply -f busybox.yaml -n busybox

Command
**# kubectl exec -it  busybox -- nc -zv <nginxpod ip> 80

**# kubectl exec -it  busybox -n busybox -- nc -zv 192.168.146.196 80

While running the above command you will observe that we are not able to reach the nginx pod. This is because nginx namespace is not part of the global deny policy and hence all the ingress (incoming) traffic to nginx namespace will be denied.

