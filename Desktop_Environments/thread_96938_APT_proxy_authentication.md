---
title: "APT proxy authentication?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by tecslicer on 2005-11-29
OK I just swiched from Fedora 4 to ubuntu. I am at college where we hid behind a proxy that needs a user name and pasword to let any thing through. so how do I get APT to update my programs?

whenever I try to install a new program from APT I get this error:

... 407 proxy authentication required (the ISA requires authentication to fullfill the request)

I have tried putting this in my apt.conf file:

Acquire::http::Proxy "http://usernamet:password@proxy_IP:8080";

I have tried every combo with it. sometimes taking things out, or putting in just the IP. whatever. I have also tried it in Synaptic but to no avail.

Sofar I love Ubuntu but it would be so much cooler if I could install programs the easy way.

---

### Post by anuda on 2006-05-16
[QUOTE=tecslicer]OK I just swiched from Fedora 4 to ubuntu. I am at college where we hid behind a proxy that needs a user name and pasword to let any thing through. so how do I get APT to update my programs?

whenever I try to install a new program from APT I get this error:

... 407 proxy authentication required (the ISA requires authentication to fullfill the request)

I have tried putting this in my apt.conf file:

Acquire::http::Proxy "http://usernamet:password@proxy_IP:8080";

I have tried every combo with it. sometimes taking things out, or putting in just the IP. whatever. I have also tried it in Synaptic but to no avail.

Sofar I love Ubuntu but it would be so much cooler if I could install programs the easy way.[/QUOTE]

I'm facing exactly similar problem. I shifted from FC5 to ubuntu Dapper, but I too face the same proxy authentication problem. Does someone have a solution ??

---

### Post by jezster on 2006-05-16
I downloaded NTLM proxy ver 0.9.9 and populated its server.cfg file.  Then ran the ./main.py file which creates a proxy on 127.0.0.1:5865.

Then issued the following:

sudo export http_proxy=http://127.0.0.1:5865
sudo export https_proxy=https://127.0.0.1:5865
sudo apt-get update && apt-get dist-upgrade

Cheers

Jeremy.

---

### Post by cakmin on 2006-10-18
> **jezster said:**
> I downloaded NTLM proxy ver 0.9.9 and populated its server.cfg file.  Then ran the ./main.py file which creates a proxy on 127.0.0.1:5865.

Then issued the following:

sudo export http_proxy=http://127.0.0.1:5865
sudo export https_proxy=https://127.0.0.1:5865
sudo apt-get update && apt-get dist-upgrade

Cheers

Jeremy.

I installed ntlm aps and tried put the commands you typed above. Still no luck and I cannot update my 6.06 using apt-get.

---

