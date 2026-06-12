---
title: "How to get rid of the kernel screen?"
date: 2008-12-10
forum: General Help
---

### Post by jcm4 on 2008-12-10
I am solely running Ubuntu 8.10 on my hard drive, and would like to skip the screen where you choose what kernel you want so I could boot straight into Ubuntu. thanks.

---

### Post by PocketDog on 2008-12-10
```
gksudo gedit /boot/grub/menu.lst
``` back this file up first (save as menu.lst.bak) and then find **# hiddenmenu**. Remove the '#', save, reboot.

---

