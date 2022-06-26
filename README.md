# hdt-buddy

## dead simple reverse proxy with hetzner dns letsencrypt challenge

### Usage in docker compose
**If you want to persist certificates, create a volume for /acme.json**
**You'll first need to create the acme.json file**
```yaml
  hdt-buddy:
    image: schieberegister/hdt-buddy:latest
    ports:
      - ${IP:?err}:80:80
      - ${IP:?err}:443:443
    environment:
      - PORT=80
      - FQDN=${FQDN:?}
      - UPSTREAM=${UPSTREAM:?} // the container or website
      - HETZNER_API_KEY=${HETZNER_API_KEY:?}
      - TRAEFIK_CERTIFICATESRESOLVERS_LE_ACME_EMAIL=${ACMEMAIL:?}
```