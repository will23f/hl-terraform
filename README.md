# hl-terraform

## GitHub repository management

Use Terraform to manage the homelab repos' GitHub settings and collaborator access. Start with a disposable repository to practice importing existing infrastructure and reviewing changes before managing the homelab repos. [GitHub provider documentation](https://registry.terraform.io/providers/integrations/github/latest/docs)

### Practice on a disposable repo

1. Create a throwaway repo in GitHub. Define it with a `github_repository` resource and a Terraform import block.
2. Run `terraform plan`. Match the existing settings so the plan proposes only the import. Apply the import, then verify that a fresh plan shows no changes.
3. Change a merge setting in GitHub. Run another plan, explain the drift, and apply the reviewed plan to restore the setting declared in Terraform. [Terraform import guide](https://developer.hashicorp.com/terraform/language/import/single-resource)

### Adopt the homelab repos

1. Import the four existing homelab repos. Capture their current visibility and merge settings, and confirm a no-change plan after import.
2. Set `hl-terraform` to private and declare the intended collaborator on all four repos with `github_repository_collaborator`. Review the plan for the visibility update and collaborator grants.
3. Apply the reviewed plan and verify repository visibility and invitation status in GitHub. The collaborator accepts the invitations to get access. [Repository resource](https://registry.terraform.io/providers/integrations/github/latest/docs/resources/repository) · [Collaborator resource](https://registry.terraform.io/providers/integrations/github/latest/docs/resources/repository_collaborator)

Commit the Terraform configuration and provider lock file. Keep GitHub credentials and Terraform state outside Git. Use a shared backend with state locking when multiple people need to apply.
