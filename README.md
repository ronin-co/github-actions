# RONIN GitHub Actions and Workflows

A collection of reusable GitHub Workflows and Actions designed to streamline processes across RONIN’s internal repositories.


## Usage

To get started, you'll need to configure the `NPM_TOKEN_READ_AND_WRITE`. This token can be obtained by creating an access token through your NPM account. All other necessary credentials are already configured as organization-wide secrets shared across all repositories.


### Example

```yaml
name: Remove Experimental Packages

on:
pull_request:
    branches:
    - main
    types: [closed]

jobs:
remove-experimental:
    uses: ronin-co/github-actions/.github/workflows/remove-experimental.yml@main
    with:
    branch_name: ${{ github.event.pull_request.head.ref }}
    package_dir: './'  # Adjust if needed
    secrets:
    NPM_TOKEN_READ_AND_WRITE: ${{ secrets.NPM_TOKEN_READ_AND_WRITE }}
    ORG_GH_RONIN_APP_ID: ${{ secrets.ORG_GH_RONIN_APP_ID }}
    ORG_GH_RONIN_PRIVATE_KEY: ${{ secrets.ORG_GH_RONIN_PRIVATE_KEY }}
```
