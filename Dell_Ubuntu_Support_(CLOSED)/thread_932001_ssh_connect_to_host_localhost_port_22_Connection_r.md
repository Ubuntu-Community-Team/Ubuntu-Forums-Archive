---
title: "ssh: connect to host localhost port 22: Connection refused"
date: 2008-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gbazuin on 2008-09-27
I'm trying to get ssh running on 8.04.

I was following [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
and only got as far as ssh localhost
I looked at the man page and did 
$ ssh -v -v -v localhost
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug2: fd 3 setting O_NONBLOCK
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused

I opened Firestarter on on the policy tab for allow service I've got 
SSH 22 everyone.

What should I try from here?

Thanks, Gary

---

### Post by rsambuca on 2008-09-27
Is the pc you are trying to connect to behind a router?  If so, you will probably have to forward port 22.

---

### Post by gbazuin on 2008-09-28
Turns out that openssh-server wasn't intalled even though which ssh showed ssh was there. Once I installed openssh-server it could connect to localhost. Still haven't got it to connect 2 computers, but I'll start reading the linksys docs to figure that out. Thanks for the help.

---

