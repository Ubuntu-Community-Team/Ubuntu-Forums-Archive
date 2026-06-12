---
title: "[SOLVED] Debian base install?"
date: 2008-08-26
forum: Debian
---

### Post by swoll1980 on 2008-08-26
I installed the Debian base system on my computer. I have nothing installed yet not even a desktop environment. When I log into the computer I go into a x terminal session, but when I try to use apt-get it ask for a cd. I was wondering if anyone could tell me how to enable the internet repos from the command line, or disable the cd repos what ever one I would have to do. thanks

---

### Post by p_quarles on 2008-08-26
Log into root and run:
```
nano /etc/apt/sources.list
```
Place a # symbol in front of the cd-rom line, and save and exit. Then run:
```
apt-get update
```
and you're all set. 

Same as in Ubuntu. ;)

---

### Post by swoll1980 on 2008-08-26
> **p_quarles said:**
> Log into root and run:
```
nano /etc/apt/sources.list
```
Place a # symbol in front of the cd-rom line, and save and exit. Then run:
```
apt-get update
```
and you're all set. 

Same as in Ubuntu. ;)

Thanks :roll: I don't know why I didn't think to comment those out #-o

---

