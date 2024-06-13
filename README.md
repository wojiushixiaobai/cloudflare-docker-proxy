# cloudflare-docker-proxy

![deploy](https://github.com/wojiushixiaobai/cloudflare-docker-proxy/actions/workflows/deploy.yaml/badge.svg)

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/wojiushixiaobai/cloudflare-docker-proxy)

> If you're looking for proxy for helm, maybe you can try [cloudflare-helm-proxy](https://github.com/ciiiii/cloudflare-helm-proxy).

## Deploy

1. fork this project
2. modify the link of the above button to your fork url
3. click the button, you will be redirected to the deploy page

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/wojiushixiaobai/cloudflare-docker-proxy)

## Config tutorial

1. use cloudflare worker host: only support proxy one registry
   ```javascript
   const routes = {
     "${workername}.${username}.workers.dev/": "https://registry-1.docker.io",
   };
   ```
2. use custom domain: support proxy multiple registries route by host
   - host your domain DNS on cloudflare
   - add `A` record of xxx.example.com to `192.0.2.1`
   - deploy this project to cloudflare workers
   - add `xxx.example.com/*` to HTTP routes of workers
   - add more records and modify the config as you need
   ```javascript
   const routes = {
     "docker.proxyapp.uk": "https://registry-1.docker.io",
     "quay.proxyapp.uk": "https://quay.io",
     "gcr.proxyapp.uk": "https://k8s.gcr.io",
     "k8s-gcr.proxyapp.uk": "https://k8s.gcr.io",
     "ghcr.proxyapp.uk": "https://ghcr.io",
   };
   ```

