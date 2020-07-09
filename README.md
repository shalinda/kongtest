
### atlas cluster -> namespace oidc-test
> How to apply remove and port forward from cluster

```
kn oidc-test
k apply -f hellowworld.yml
k delete -f hellowworld.yml
k port-forward service/helloworld-svc 8080:80
```

### Kong kubenates ingress setup
```
k apply -f helloworld1.yaml

export pod=helloworld-svc- #pod name
k exec -it $pod /bin/sh
mkdir -p /usr/share/nginx/html/api/v1/mono1/

k cp service1.json $pod:/usr/share/nginx/html/api/v1/mono1/

curl http://oidctest1.atlas.nonprod.torq.trans.apps.ge.com/api/v1/mono1/service1.json
# Should return the json
```

# Trace logs in kong ingress controller
```
kn torq-system
export kong-ing=kong-ingress-controller- #pod name
k logs -f $kong-ing -c ingress-controller --tail=100
```
# kongtest
