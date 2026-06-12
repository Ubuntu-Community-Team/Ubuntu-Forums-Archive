---
title: "Only shell prompt - Graphical desktop not showing up"
date: 2008-05-21
forum: Desktop Environments
---

### Post by Srikanth.Vittal on 2008-05-21
Hi

I have Ubuntu 7.10. It was working fine. When I uninstalled "gnome-keywring" the system automatically restarted and it shows up only shell prompt asking for login! No GUI Desktop shows up. No error shows up. After I login, I tried "startx". It starts, but hangs! Could anyone help me in fixing this issue?

Thanks
Srikanth

---

### Post by thorcik on 2008-05-21
if you remove gnome-keyring some more packages are removed too, one of those is ubuntu-desktop. so I think You should do this:
```
sudo apt-get install ubuntu-desktop
```
and all should be fine. at least that's what I would do.

---

