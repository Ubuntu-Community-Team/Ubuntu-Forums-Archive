---
title: "ssh issue: ssh_exchange_identification"
date: 2009-01-18
forum: General Help
---

### Post by chris4585 on 2009-01-18
So I'm trying to connect to my arch desktop from my ubuntu laptop, I get this.  I've looked around but nothing has helped

chris@chris-laptop:~$ ssh chris@192.168.1.101 -v
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.101 [192.168.1.101] port 22.
debug1: Connection established.
debug1: identity file /home/chris/.ssh/identity type -1
debug1: identity file /home/chris/.ssh/id_rsa type -1
debug1: identity file /home/chris/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
chris@chris-laptop:~$

---

### Post by Nepherte on 2009-01-18
It seems more like a problem with the server than the laptop. I had a similar problem with my ssh arch setup and you have to allow incoming connections for the ssh daemon. Open /etc/hosts.allow on your ssh server:
```
gksudo gedit /etc/hosts.allow
```
and add the following line:
```
sshd: ALL
```
You can restrict access by replacing ALL with specific ip addresses or network addresses and network masks.

---

### Post by chris4585 on 2009-01-18
Yeah, I've tried that too, nothing worked

thanks for the reply Nepherte

---

### Post by chris4585 on 2009-01-18
problem fixed, it was my own stupidity, I looked in host.deny and nothing was in there, then I saw it was hosts.deny, so I cleared what was in that file and it worked

---

