---
title: "which app to track bandwidth?"
date: 2005-09-16
forum: Desktop Environments
---

### Post by pesachzon on 2005-09-16
Hi,
Lately i've noticed that my upload rate is higher than it should be, is there a program which I can use to find out which programs are uploading/downloading and at which bandwidth?

thanks

---

### Post by KingBahamut on 2005-09-16
You can use iptraf and etherape to track packet usage. 

apt-get install iptraf etherape 

Etherape is a graphical star spread of network traffic. 
iptraf is an ncurses based console utility to track packets on the Ip address and port level. 

Youll need to be root as either to use them, and Id drop your eth interface into promiscuous mode so youll pickup all the packets.

---

### Post by pesachzon on 2005-09-16
thanks

---

