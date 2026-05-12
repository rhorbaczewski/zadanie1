# Zadanie 1 dodatkowe PAwChO

Robert Horbaczewski

1. (max +20%)

Utworzenie buildera:
```bash
docker buildx create --name zadanie1builder --driver docker-container --use --bootstrap
```

Budowanie obrazu wieloarchitekturowego:
```bash
docker buildx build --platform linux/amd64,linux/arm64 -t roberthorbaczewski/zadanie1:v2.0.0 --push .
```

Sprawdzenie manifestu:
```bash
(base) roberthorbaczewski@MacBook-Air-M2-Robert zadanie1 % docker buildx imagetools inspect roberthorbaczewski/zadanie1:v2.0.0
Name:      docker.io/roberthorbaczewski/zadanie1:v2.0.0
MediaType: application/vnd.oci.image.index.v1+json
Digest:    sha256:a58359a021623c3603ed342f9b9bc6c75300eb50a1c5b580e9d2573c70c8cfc1
           
Manifests: 
  Name:        docker.io/roberthorbaczewski/zadanie1:v2.0.0@sha256:3f36658cf6932b8c2baa29f80fb871e29e4ea90f6e4b11b4e0a250fd4ab80bf1
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    linux/amd64
               
  Name:        docker.io/roberthorbaczewski/zadanie1:v2.0.0@sha256:155fc5b7a331ce47b474d2ffa85798d39f16048a24e66e1c33fa4622c0afebc6
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    linux/arm64
               
  Name:        docker.io/roberthorbaczewski/zadanie1:v2.0.0@sha256:f913efaa8bf930f88e8ce5733f1642efe85014d9f43a0cab6c4d69881e97f071
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    unknown/unknown
  Annotations: 
    vnd.docker.reference.digest: sha256:3f36658cf6932b8c2baa29f80fb871e29e4ea90f6e4b11b4e0a250fd4ab80bf1
    vnd.docker.reference.type:   attestation-manifest
               
  Name:        docker.io/roberthorbaczewski/zadanie1:v2.0.0@sha256:cd50f32a1c1b6c598d43196b964cceeb1fca189d74e1ecc5d72fdb2223e1b433
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    unknown/unknown
  Annotations: 
    vnd.docker.reference.digest: sha256:155fc5b7a331ce47b474d2ffa85798d39f16048a24e66e1c33fa4622c0afebc6
    vnd.docker.reference.type:   attestation-manifest
```

Analiza podatności CVE - brak zagrożeń CRITICAL/HIGH
```bash
docker scout cves zadanie1
```
![Screenshot](screenshot2.png)
