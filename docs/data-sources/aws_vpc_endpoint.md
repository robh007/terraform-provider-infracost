# infracost_aws_vpc_endpoint

Provides estimated data processing through an AWS VPC `Interface` or `GatewayLoadBalancer` endpoint.

## Example Usage

```hcl
resource "aws_vpc_endpoint" "vpc_endpoint" {
  vpc_id = "vpc-123456"
  service_name = "my-vpc-endpoint-service"
}

data "infracost_aws_vpc_endpoint" "vpc_endpoint_costs" {
  resources = list(aws_vpc_endpoint.vpc_endpoint.id)

  monthly_gb_data_processed {
    value = 1000
  }
}
```

## Argument Reference

* `resources` - (Required) The IDs of the VPC Endpoint to apply the estimated dat processing cost.
* `monthly_gb_data_processed` - (Optional) The estimated monthly data processing in GB.

### Usage values

Each of the usage value blocks currently supports the following attributes:
* `value` - (Optional) The estimated value.
