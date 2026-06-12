---
title: "stop ntp server"
date: 2009-01-29
forum: General Help
---

### Post by lex1 on 2009-01-29
how do I stop a ntp server running 

lex1

---

### Post by rwstoner on 2009-01-29
> **lex1 said:**
> how do I stop a ntp server running 

lex1

If you want to stop it as a running service then you will type one of these:

sudo /etc/init.d/ntp stop
sudo /etc/init.d/ntp-server stop
sudo /etc/init.d/ntpd stop

If you would like to remove the program all together then type one of these:

sudo apt-get remove ntp
sudo apt-get remove ntp-server
sudo apt-get remove ntpd

Each command depends on what version of ntp you have installed.

---

