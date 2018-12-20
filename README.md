# quickstart-trek10-serverless-enterprise-cicd

## Best practices to follow
https://aws-quickstart.github.io/reqs.html
https://aws-quickstart.github.io/best-practices.html#linux

## Questions for AWS Quick Start team
What should we do about the named roles in the cross account scripts? We could add some identifiers like region or account id to the named roles to prevent collisions in other regions

## TODO
- [x] cross account roles
- [x] determine what to do with named roles
- [x] account infrastructure
- [x] base pipeline
- [ ] dynamic feature branches
- [x] base app with SAM template
- [ ] testing
- [ ] ssm param store integration
- [ ] secrets manager integration
- [ ] refactor
- [ ] run taskcat

## Assumptions
Cross account role access is implicitly created using the app name and AWS region being deployed into. It would be more ideal to use FN::ImportValue but can't do that cross account.

## Useful commands
```
aws cloudformation validate-template --template-body file://account.yaml
aws cloudformation deploy --template-file account.yaml --stack-name sample-pipeline-account --capabilities CAPABILITY_NAMED_IAM

aws cloudformation validate-template --template-body file://cross-account.yaml
aws cloudformation deploy --template-file cross-account.yaml --stack-name sample-pipeline-cross-account --capabilities CAPABILITY_NAMED_IAM

aws cloudformation validate-template --template-body file://pipeline.yaml
aws cloudformation deploy --template-file pipeline.yaml --stack-name sample-pipeline
```