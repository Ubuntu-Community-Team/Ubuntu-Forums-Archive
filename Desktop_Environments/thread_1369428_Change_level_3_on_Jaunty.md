---
title: "Change level 3 on Jaunty"
date: 2010-01-01
forum: Desktop Environments
---

### Post by mzainal on 2010-01-01
Hi,

I want to know how to change level 3 on jaunty? I use desktop version for my server.

Thank you.

---

### Post by SalahTr on 2010-01-01
Hi mzainal,

To change to runlevel 3 execute :
```
sudo telinit 3
```
However under Ubuntu runlevels 2, 3, 4 and 5 all set up as standard multiuser mode and graphical login. If you need console logins only execute:
```
sudo update-rc.d -f gdm remove
```

---

