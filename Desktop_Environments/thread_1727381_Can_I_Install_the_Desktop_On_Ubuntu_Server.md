---
title: "Can I Install the Desktop On Ubuntu Server"
date: 2011-04-12
forum: Desktop Environments
---

### Post by Greg93 on 2011-04-12
I like the GUI of Ubuntu Desktop and the LAMP server install.
 
Greg

---

### Post by james_xxx on 2011-04-12
Yes.

All you would need to do is install the meta-package for the desktop environment you want.

For Gnome:
```
sudo apt-get install ubuntu-desktop
```

For KDE:
```
sudo apt-get install kubuntu-desktop
```

For XFCE:
```
sudo apt-get install xubuntu-desktop
```

Your server installation is essentially just a base installation, without GUI, along with some tools that would likely be needed in a server-type environment.

---

