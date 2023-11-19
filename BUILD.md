## Build

```bash
podman build -t tsamaya/curl .
```

## Publish package

1- Authentication
https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry#authenticating-with-a-personal-access-token-classic

```bash
export CR_PAT=YOUR_TOKEN
echo $CR_PAT | podman login ghcr.io -u USERNAME --password-stdin

```

2- Tag

```bash
TAG=$(date +"%Y%m%d").$$

podman tag localhost/tsamaya/curl:latest ghcr.io/tsamaya/curl:latest
podman tag localhost/tsamaya/curl:latest ghcr.io/tsamaya/curl:${TAG}
```

3- Pushing
https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry#pushing-container-images

```bash
podman push ghcr.io/tsamaya/curl:latest
# if TAG
podman push ghcr.io/tsamaya/curl:${TAG}

```
