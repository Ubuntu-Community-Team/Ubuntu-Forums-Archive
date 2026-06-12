---
title: "[SOLVED] gdmsetup--how to install it"
date: 2007-09-03
forum: Desktop Environments
---

### Post by shortybookit on 2007-09-03
Drag and drop this theme into the gdmsetup tool to install

were is the gdmsetup tool

if i do not have it how do i install it/

---

### Post by tomcheng76 on 2007-09-03
you need GDM - GNOME Display Manager
to install:
```
 sudo apt-get install gdm 
```
to configure your system to use gdm as default
```
 sudo dpkg-reconfigure gdm 
```
then run gdmsetup as root to install theme or login manager
```
 sudo gdmsetup 
```

---

