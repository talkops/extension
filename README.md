# talkops-extension

A GitHub Action to build, push, and publish the TalkOps Extension.

## Overview

The `talkops-extension` GitHub Action automates the process of building, pushing, and publishing Docker images for the TalkOps Extension. It performs the following steps:

1. **Checkout Repository**: Clones the repository to the runner.
2. **Set up QEMU**: Initializes QEMU for cross-platform builds.
3. **Set up Docker Buildx**: Configures Docker Buildx with the `docker-container` driver for multi-platform support.
4. **Authenticate with GHCR**: Logs into the GitHub Container Registry (GHCR) using the provided credentials.
5. **Extract Docker Image Tag**: Determines the Docker image tag from the current GitHub tag reference.
6. **Build and Push Docker Image**: Builds and pushes the Docker image to GHCR for multiple platforms.
7. **Notify GitHub ETL**: Sends a notification to the GitHub ETL with repository and tag information.

## Usage

To use this action in your repository, add it to your workflow file:

```yaml
name: TalkOps Extension
on:
  push:
    tags:
      - 'v*'
jobs:
  talkops:
    runs-on: ubuntu-latest
    permissions:
      packages: write
    steps:
      - uses: talkops/extension@v1
```
