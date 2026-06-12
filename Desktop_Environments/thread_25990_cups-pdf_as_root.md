---
title: "cups-pdf as root"
date: 2005-04-11
forum: Desktop Environments
---

### Post by brickbat on 2005-04-11
Can someone please give me the command to allow cups-pdf to run as root.

ciao
bb

---

### Post by cfa on 2005-04-18
edit :

nano /etc/cups/cupsd.conf

replace :

RunAsUser? No => Yes

save

restart :

/etc/init.d/cupsys restart

---

### Post by brickbat on 2005-04-21
thanks

---

