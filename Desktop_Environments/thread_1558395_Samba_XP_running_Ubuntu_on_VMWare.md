---
title: "Samba XP running Ubuntu on VMWare"
date: 2010-08-22
forum: Desktop Environments
---

### Post by cymorg on 2010-08-22
I have an XP workstation using VMWare Player to host Ubuntu 10.04.

Ping and web browsing working perfectly but samba is unable to connect.  I've done nothing on the XP machine except allow sharing of a single folder. Do I need to do more?

---

### Post by cymorg on 2010-08-22
Turns out you need to use NAT rather than bridged connection in VMWare - shouldn't need to do this but it seems to work.

---

