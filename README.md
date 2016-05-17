# RRS-converter Go

This script allows you to simply convert AWS S3 objects to Reduce Redundancy Storage class. This is useful, if you want to safe some money.

Script leverages
[AWS-sdk](https://github.com/aws/aws-sdk-go)
and some magic of goroutines to convert all objects in S3 bucket to RRD-storage class. If you want to convert only some of them, feel free to modify this script or use
[AWS CLI](http://www.developmentshack.com/amazon-s3-command-line-optionstipstricks/42).

### Build and install
##### Dependencies:
- [AWS-sdk](https://github.com/aws/aws-sdk-go)
- [Terminal progress bar for Go](https://github.com/cheggaaa/pb)


##### Installation:
Script is written in Go 1.6. Installation:
```
$ git clone https://github.com/grem11n/rrs-converter-go.git
$ go build rrs-converter.go
```

### Usage

- You must specify which bucket to convert with `-bucket` flag. This is the only parameter, which is strictly required

##### Optional parameters:

- `-config` - custom config location. I've never tried it with relative path. It could probably works, who knows. If not declared, AWS-sdk use your `~/.aws/credentials` file by default
- `-region` - bucket location. Script will use `us-east-1` by default
- `-section` specifies which section of your AWS configuration file to use. If not specified, use "[default]"
- `-maxcon` - number of maximum concurrent goroutines. 10 by default

### Example

```
rrs-converter.go -bucket=my-bucket -config="/home/user/.aws/credentials" -region=eu-west-1 -section=test -maxcon=5
```

### TODO:

- [ ] Fix logging for converter func
