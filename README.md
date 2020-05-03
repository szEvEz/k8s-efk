Based on https://www.digitalocean.com/community/tutorials/how-to-set-up-an-elasticsearch-fluentd-and-kibana-efk-logging-stack-on-kubernetes, but actually working tho

```sh
gcloud auth login
gcloud config set project $PROJECT
gcloud container clusters get-credentials $CLUSTERNAME --zone $YOURZONE --project $PROJECT

alias k='kubectl'
k config set-context --current --namespace=logging

k apply -f elasticsearch.yaml
k apply -f kibana.yaml
k apply -f fluentd.yaml

k get po
k port-forward kibanapod 5601:5601
visit localhost:5601
```