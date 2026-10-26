# One-Click Release Pipeline

Sample app with a **GitHub Actions** pipeline: test → build image → security scan → publish artifact.

## What this demonstrates

| Step | Purpose |
|------|---------|
| Lint & test | Catch bugs before merge |
| Docker build | Reproducible runtime |
| Trivy scan | Block images with critical CVEs |
| Artifact upload | Traceable build output |

## Run locally

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
pytest
python app/main.py
```

Open http://127.0.0.1:8080 — you should see `{"status":"ok","service":"release-pipeline-demo"}`.

## Docker

```bash
docker build -t release-pipeline-demo .
docker run --rm -p 8080:8080 release-pipeline-demo
```

## CI/CD

Workflow: [`.github/workflows/ci.yml`](.github/workflows/ci.yml)

Push to `main` to run the full pipeline on GitHub Actions.
