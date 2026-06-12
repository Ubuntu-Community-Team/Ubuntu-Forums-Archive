---
title: "Text login"
date: 2006-04-16
forum: Desktop Environments
---

### Post by utab on 2006-04-16
dear all,

Could anyone tell me how to change to the text login in Ubuntu??

I tried with the initdefault line set to 3 in /etc/inittab file but no use still the graphical login??

Thx.

---

### Post by Ramses de Norre on 2006-04-16
sudo apt-get install sysv-rc-conf && sudo sysv-rc-conf
Uncheck gdm (or kdm whatever you use) for runlevel 2

---

