ECS File Deploy.
================


Like [ECS Deploy](https://github.com/silinternational/ecs-deploy) except uses a JSON ECS definition file for infrastructure as code.


```
Script for triggering blue/green deployments on Amazon Elastic Container Service given a specific Task Definition JSON file.

Required arguments:
    -k | --aws-access-key        AWS Access Key ID. May also be set as environment variable AWS_ACCESS_KEY_ID
    -s | --aws-secret-key        AWS Secret Access Key. May also be set as environment variable AWS_SECRET_ACCESS_KEY
    -r | --region                AWS Region Name. May also be set as environment variable AWS_DEFAULT_REGION
    -p | --profile               AWS Profile to use - If you set this aws-access-key, aws-secret-key and region are needed
    -c | --cluster               Name of ECS cluster
    -n | --service-name          Name of service to deploy
Optional arguments:
    -f | --task-file             Default is 'ecs-service.json'. Filename of the configured ECS task definition file.
    -t | --timeout               Default is 90s. Script monitors ECS Service for new task definition to be running.
    -v | --verbose               Verbose output
Requirements:
    aws:  AWS Command Line Interface
    jq:   Command-line JSON processor
Examples:
  Simple deployment of a service (Using env vars for AWS settings):
    ecs-file-deploy -c production1 -n doorman-service
  All options:
    ecs-file-deploy -k ABC123 -s SECRETKEY -r us-east-1 -c production1 -n doorman-service -f doorman-definition.json -t 240 -v
  Using profiles (for STS delegated credentials, for instance):
    ecs-file-deploy -p PROFILE -c production1 -n doorman-service
```

