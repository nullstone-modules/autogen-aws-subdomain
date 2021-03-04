# block-ns-aws-subdomain

Nullstone Block creating an AWS Subdomain (e.g. `random-slug.nullstone.app`) with a Nullstone-managed root domain (`nullstone.app`). 

## Inputs

- `subdomain: string`
  - This represents the token to prepend the input domain block (i.e. the fqdn is represented by {var.subdomain}.<domain>.)
  - Example: `subdomain = random-slug` will create `random-slug.nullstone.app`
- `create_vanity: bool`
  - default: `false`
  - Enable this to create a vanity subdomain instead of environmental. This is typically enabled on the production environment.
- `create_cert: bool`
  - default: `true`
  - Enable this to create an SSL certificate through AWS ACM service.

## Outputs

- `name: string` - The created subdomain.
- `zone_id: string` - The zone ID of the AWS Route53 Zone for the created subdomain.
- `nameservers: list(string)` - The list of nameservers of the AWS Route53 Zone for the created subdomain.
- `domain_name: string` - The name of the root domain.
- `domain_zone_id: string` - The zone ID of the root domain.
- `cert_arn: string` - If var.create_cert is enabled, the ARN of the SSL Certificate.