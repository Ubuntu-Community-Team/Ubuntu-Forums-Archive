---
title: "Shell Script to Generate SSL Cert Request on remote host"
date: 2009-04-14
forum: General Help
---

### Post by ecrossahoo on 2009-04-14
Hello,

My question is not so much about SSL Cert Requests, it's about how to create a script to generate SSL certificate requests on a remote host.

Below is my stab at this, but I cannot figure out how to pass the requested arguments into the openssl command correctly.  I have a major problem with redirecting the "answers" into the openssl cert request.  "hostlist" would contain any hosts that need the certificate signed.


#!/bin/sh
#
Country=US
State=CA
City=San Jose
Organization=Engineering
Host=""
Email=" "
for i in `cat hostlist`
do
  ssh $i "sudo openssl genrsa -rand -des3 -out /tmp/serverkey.$i 1024 -config /use/share/ssl/openssl.cnf"
  Host="$i"  
  echo $Country > /tmp/cert-data
  echo $State >> /tmp/cert-data
  echo $City >> /tmp/cert-data
  echo $Organization >> /tmp/cert-data
  echo $Host >> /tmp/cert-data
  echo $Email >> /tmp/cert-data
  scp /tmp/cert-data certuser@$i:/tmp/cert-data
  ssh $i sudo openssl req -new -key /tmp/serverkey.$i -out /tmp/server.csr.$i -config /usr/share/ssl/openssl.cnf < /tmp/cert-data
done


Once I get that to work, I can scp the /tmp/serverkey.$i to my Cert Authority and sign it.

Thank You.

---

### Post by ecrossahoo on 2009-04-16
Following up here.

openssl has a -batch switch which avoids being prompted for the answers.  That allowed me to kick off the certificate request easily enough.

I used the following to dynamically update my openssl.cnf for each host:

```
for i in `cat $HOSTLIST`
do
  echo '======'
  echo "$i"
  /usr/local/bin/sudo sh -c " sed 's/commonName_default          = .*/commonName_default          = $i/g' $OPENSSLCNF > $SIGNREQS/tmpfile && /usr/local/bin/sudo mv $SIGNREQS/tmpfile $OPENSSLCNF"
  /usr/local/bin/sudo openssl req -new -nodes -key $CERTREQS/$i.key -out $SIGNREQS/$i.csr -config $OPENSSLCNF -batch
done
```

---

