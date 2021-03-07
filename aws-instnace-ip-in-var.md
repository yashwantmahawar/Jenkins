# Jenkins use aws instance ip's in variable

```groovy
def sout = new StringBuilder(), serr = new StringBuilder()
def command = 'aws ec2 describe-instances --region ap-south-1 --filters Name=tag:env,Values=nonprod  \
--query Reservations[*].Instances[0].PrivateIpAddress --output text --profile paytmreadonly'

def proc = command.execute()
proc.consumeProcessOutput(sout, serr)

proc.waitForOrKill(10000)
sout = "* " + sout
return sout.tokenize()
```
