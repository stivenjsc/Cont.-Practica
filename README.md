# Cont.-Practica

Practica de CI/CD con Docker y GitHub Actions para:

1. Construir y subir imagen Docker a Docker Hub.
2. Desplegar automaticamente en Render al hacer push a `main`.

## Pipeline

El workflow esta en `.github/workflows/ci-cd.yml` y se ejecuta en:

1. `push` a `main`
2. Ejecucion manual con `workflow_dispatch`

## Secrets requeridos en GitHub

Configura estos secrets en tu repositorio (`Settings > Secrets and variables > Actions`):

1. `DOCKERHUB_USERNAME`: usuario de Docker Hub.
2. `DOCKERHUB_TOKEN`: access token de Docker Hub.
3. `DOCKERHUB_REPOSITORY`: nombre del repositorio en Docker Hub (ejemplo: `cont-practica`).
4. `RENDER_API_KEY`: API key de Render.
5. `RENDER_SERVICE_ID`: ID del servicio en Render.

## Resultado esperado

En cada push a `main`:

1. Se construye la imagen Docker.
2. Se publica en Docker Hub con tags `latest` y `sha-<commit>`.
3. Se llama la API de Render para crear un nuevo deploy.