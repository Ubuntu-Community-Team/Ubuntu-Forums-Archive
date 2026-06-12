---
title: "more woes.  Slow responding DNS"
date: 2005-10-22
forum: Desktop Environments
---

### Post by duffydack on 2005-10-22
I had Hoary on previously.  I then put breezy on and after the "686-smp" problem i went back to hoary, but now it takes a couple of seconds for anything internet related to respond.  DNS. 
The way its acting is like its takin too long to resolve dns.  resolve has correct entry for my router/dns (192.168.1.1)
It was fine before, is ok in windows, routers ok, everythings ok apart from hoary.
Any setting that would help?

tia

---

### Post by codejunkie on 2005-10-22
[quote=duffydack]I had Hoary on previously.  I then put breezy on and after the "686-smp" problem i went back to hoary, but now it takes a couple of seconds for anything internet related to respond.  DNS. 
The way its acting is like its takin too long to resolve dns.  resolve has correct entry for my router/dns (192.168.1.1)
It was fine before, is ok in windows, routers ok, everythings ok apart from hoary.
Any setting that would help?

tia[/quote] it could be ipv6 related, it seems to slow networking down on my system quite a bit you could try disabling it like this, open a terminal and copy and paste this in there 
```
sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases-backup
``` then
```
sudo gedit /etc/modprobe.d/aliases
```find this line  
```
alias net-pf-10 ipv6
``` and change it to ```
alias net-pf-10 off
``` save the file and reboot hope it helps.

---

### Post by duffydack on 2005-10-22
thanks

---

### Post by duffydack on 2005-10-23
nope. hasnt fixed anything.  Weird, as its never happend on any version of linux, even kubuntu.  Till now.
its friggin annoying

---

