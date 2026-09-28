# Automated CI/CD Pipeline with GitHub Actions

![CI/CD Pipeline](https://github.com/YOUR_USERNAME/YOUR_REPOSITORY/actions/workflows/ci-cd.yml/badge.svg)

A simple Flask application demonstrating an automated CI/CD pipeline with GitHub Actions.

## Pipeline

The workflow runs automatically on:

- Pull requests targeting `main`
- Pushes to `main`

### Stages

1. **Lint** - Runs Flake8.
2. **Unit Tests** - Runs Pytest.
3. **Docker Build & Push** - Builds the Docker image and pushes it to GitHub Container Registry (GHCR) after a successful push to `main`.

## Project Structure

```text
.
├── .github/
│   └── workflows/
│       └── ci-cd.yml
├── tests/
│   └── test_app.py
├── app.py
├── Dockerfile
├── requirements.txt
├── .dockerignore
├── .gitignore
└── README.md
```

## Run Locally

```bash
pip install -r requirements.txt
pytest -v
python app.py
```

Open:

```text
http://localhost:5000
```

Health endpoint:

```text
http://localhost:5000/health
```

## GitHub Container Registry

This workflow uses the built-in `GITHUB_TOKEN`, so no Docker Hub password is required.

After pushing to `main`, the image is published to:

```text
ghcr.io/<your-github-username>/<your-repository>:latest
```

## GitHub Setup

1. Create a GitHub repository.
2. Upload all project files.
3. Replace `YOUR_USERNAME/YOUR_REPOSITORY` in the README badge with your actual repository path.
4. Push the files to the `main` branch.
5. Open the **Actions** tab.
6. Verify that **Lint Code**, **Run Unit Tests**, and **Build and Push Docker Image** complete successfully.
7. The green checkmark and workflow logs can be used as task proof.

> Note: GHCR packages may need to be made public from the repository's Packages section if you want others to pull the image without authentication.
