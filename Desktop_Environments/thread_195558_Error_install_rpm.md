---
title: "Error install rpm"
date: 2006-06-13
forum: Desktop Environments
---

### Post by mzainal on 2006-06-13
Hello..

When I install rpm file, this error came out:

root@ubuntu:/home/banie/My Downloads# rpm -i mplayer-vidix-1.0pre8-0.7.20060406.i386.rpm
bash: rpm: command not found

Why?? How to fix it?

---

### Post by user1397 on 2006-06-13
the command is not "rpm", but actually "alien".  you need to install the package "alien" first from synaptic, and then you could install your program with 
```
alien -i mplayer-vidix-1.0pre8-0.7.20060406.i386.rpm
``` i still don't understand, however, why you would want to install mplayer this way.  can't you just install it via synaptic (system > administration > synaptic package manager)

Also, have you considered upgrading to dapper?  this would not make installing rpm's easier, but it might make many other things work smoother.

btw, deb is the packaging system for all debian-derived linux distributions (including ubuntu), and rpm is the one for all redhat-derived linux distributions (like fedora core)

---

### Post by aysiu on 2006-06-13
You would probably need root privileges: ```
sudo aptitude update
sudo aptitude install alien
sudo alien -i mplayer-vidix-1.0pre8-0.7.20060406.i386.rpm
```

---

