---
title: "not so much ubuntu as debian"
date: 2008-01-02
forum: Debian
---

### Post by russian460 on 2008-01-02
hi i have a debian server running squid so i can use it as a proxy i was wondering how do i cnage the port on it from 21 to sometihng else ? what is the command for it ?

---

### Post by ~LoKe on 2008-01-03
You should be able to change it in /etc/squid.conf.

---

### Post by russian460 on 2008-01-03
ummm and i would get there how? its been a while scince i set it up

---

### Post by Antman on 2008-01-03
> **russian460 said:**
> ummm and i would get there how? its been a while scince i set it up

open a terminal and as root start a text editor of your choice, then open the /etc/squid.conf file to edit it. 
So if you use nano as your editor, as root run:

```
nano /etc/squid.conf
```

Make your changes and save the file.

---

### Post by russian460 on 2008-01-03
umm im running debian idk if it has a text editior and is that the only port i have to change?

---

### Post by maybeway36 on 2008-01-04
You probably have nano and vi, if you don't you can type
```
apt-get install nano
```
as root to install nano.

---

### Post by jinx099 on 2008-01-05
squid's default port should be 3128, BTW.  Port 21 is for FTP.

---

