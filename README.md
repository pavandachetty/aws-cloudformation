```markdown
# aws-cloudformation
```

CloudFormation EC2 example
-------------------------

This repository now includes a simple CloudFormation template to create an EC2 instance:

- File: [ec2-instance.yaml](ec2-instance.yaml)

Quick deploy (using AWS CLI):

```bash
aws cloudformation deploy \
	--template-file ec2-instance.yaml \
	--stack-name my-ec2-stack \
	--parameter-overrides KeyName=your-key InstanceType=t2.micro
```

Notes:
- Replace `KeyName` with your EC2 KeyPair name (or omit to not attach a key).
- If you're outside `us-east-1`, supply a region-appropriate `ImageId`.

Validate the template before deploying:

```bash
aws cloudformation validate-template --template-body file://ec2-instance.yaml
```

To override the region-provided AMI, pass `ImageId` in `--parameter-overrides`:

```bash
aws cloudformation deploy \
	--template-file ec2-instance.yaml \
	--stack-name my-ec2-stack \
	--parameter-overrides KeyName=your-key InstanceType=t2.micro ImageId=ami-0123456789abcdef0
```
# aws-cloudformation