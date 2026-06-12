---
title: "Only console mode"
date: 2010-10-24
forum: Desktop Environments
---

### Post by bluelotus on 2010-10-24
I run a Anthlon 64 X2 5200+ with a on board Nvidia Gforce 6150  video card. Yesterday installed Ubuntu 10.04 64 with nomodeset ( screen would go blank during install) .Today when I tried booting it up I got the following message :

Gave up waiting .....
Missing module ( cat/proc/modules;ls/dev)
ALERT! /dev/disk/by-uuid/off5c6ff-4847-4c96-acdo-231c919ce59f

Dropping to shell.After that i get only the console .

As far as Linux is concerned I am a complete newbie . I would appreciate if someone can help me out explaining what might be wrong and what needs to be  done

---

### Post by Alessandro.g89 on 2010-10-24
Looks like you have trouble with some disk or partition. try 
```
sudo fdisk -l
```
and post the result. Also, try starting the desktop with
```
startx
```

---

