---
title: "Need help using Open Office over sftp"
date: 2008-08-03
forum: Desktop Environments
---

### Post by MountainX on 2008-08-03
I need some help understanding how to resolve this.

**Background:**
When I try to open ODT files over an sftp connection, Open Office asks for my username and password, then gives a general internet error and will not open the files.

The problem is described in this bug report:
[https://bugs.launchpad.net/openoffice/+bug/41985](https://bugs.launchpad.net/openoffice/+bug/41985)

A solution is offered in this comment:
[https://bugs.launchpad.net/openoffice/+bug/41985/comments/18](https://bugs.launchpad.net/openoffice/+bug/41985/comments/18)

Server & client both have same version of ssh:
ssh -V
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007


**Now to my question**

How safe/secure is the workaround proposed in the comment linked above? If someone got my local (private) key, they could get access to the server, right?

What is the best way to go about implementing this solution? Can I store the private key inside GPG via Seahorse? If so, how? 

Also, does setting up an SSH key pair between a client and server allow login in both directions? In other words, could I put the private key on the server and still solve my Open Office problem?
Thanks.

---

