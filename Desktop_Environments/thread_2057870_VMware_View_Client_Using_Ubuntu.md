---
title: "VMware View Client Using Ubuntu"
date: 2012-09-14
forum: Desktop Environments
---

### Post by metallica1973 on 2012-09-14
I installed the VMware View Client for Linux in Ubuntu and whenever I try and connect I recieve:

[php]Untrusted View Connection:

Failed to connect to the View Connection Server. The server provided an invalid certificate.

The certificate authority is invalid or incorrect.
[/php]

Having access to my esxi 5 server I able to pulled the rui.crt and the rui.key like what was suggested in the documentation:

[php]"NOTE For instructions on distributing a self-signed root certificate that users can install on their Linux client
systems, see the Ubuntu documentation.
View Client uses the PEM-formatted certificates stored in the /etc/ssl/certs directory on the client system.
For instructions on importing a root certificate stored in this location, see the procedure called "Importing a
Certificate into the System-Wide Certificate Authority Database" in the document at
https://help.ubuntu.com/community/OpenSSL."
[/php]

These are the steps that I did to attempt to import the root certificates and etc.

[php]1 -  Created a directory under /usr/share/ca-certificates/ , called 192.168.1.8

2 -  Added the two certificates, rui.key and rui.crt

3 - Added my paths to /etc/ca-certificates.conf

192.168.1.8/rui.crt

4 -  Update the CA certificates database

sudo update-ca-certificates
[/php]

then when I reattempted to connect to my esxi server using VMware View Client, I get the same message. I even change under preferences:

Do not verify server identity certificates and then I get a HTTP error 400

Any Ideas?

---

