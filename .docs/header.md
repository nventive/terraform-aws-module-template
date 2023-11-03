![nventive](https://nventive-public-assets.s3.amazonaws.com/nventive_logo_github.svg?v=2)

# terraform-aws-module-skeleton

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=flat-square)](LICENSE) [![Latest Release](https://img.shields.io/github/release/nventive/terraform-aws-module-skeleton.svg?style=flat-square)](https://github.com/nventive/terraform-aws-module-skeleton/releases/latest)

Terraform module to create SOMETHING.

---

## How to use

- Always run `make hooks` after cloning.
- Update `.docs/header.md` rather than `README.md`.
- Delete this "how to use" section from `.docs/header.md`.
- Update `.docs/header.md`with a viable example.
- Use the `variables.tf` file for variable declarations.
- Use the `outputs.tf` file for output declarations.
- Use the `main.tf` for all resources/data/locals declarations.
- The `context.tf` file should be downloaded
  from `https://github.com/cloudposse/terraform-null-label/blob/master/exports/context.tf`, DO NOT update that file
  manually.
- Update the `versions.tf` file with the correct dependencies.

### Enabled?

Since the enabled variable might be passed directly from the context, _always_ use the method below to determine whether
or not the module should be enabled.

```hcl
locals {
  enabled = module.this.enabled
}

# Do not use `var.enabled` directly.
resource "aws_some_resource" "default" {
  count = local.enabled ? 1 : 0 
}
```

### Before you commit

Always run the following commands _before_ you commit.

```shell
terraform fmt
make docs
```

## Examples

**IMPORTANT:** We do not pin modules to versions in our examples because of the difficulty of keeping the versions in
the documentation in sync with the latest released versions. We highly recommend that in your code you pin the version
to the exact version you are using so that your infrastructure remains stable, and update versions in a systematic way
so that they do not catch you by surprise.

```hcl
module "skeleton" {
  source = "nventive/module-skeleton/aws"
  # We recommend pinning every module to a specific version
  # version = "x.x.x"

  namespace = "eg"
  stage     = "test"
  name      = "app"

  # Parameters for example. 
}
```
