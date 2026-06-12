---
title: "i get GRUB error when i boot from windows HD"
date: 2006-09-07
forum: Desktop Environments
---

### Post by mjoyce91 on 2006-09-07
i just installed ubutunu on my slave drive, and now when i try to boot into my C drive (master) with Windows, it says, GRUB Error. How do I fix this?

---

### Post by bernied on 2006-09-07
Please post the results of these commands and I'll try to help. Type the commands in a terminal window (I think that's in the system menu on Ubuntu. And to cut and paste you just highlight the text to copy, then click both mouse buttons - or middle button if you got one - to paste.):
```
cat /boot/grub/menu.lst
sudo fdisk -l
```
The first command lists the config file for the bootloader, the second lists your disk drive configuration.

In case you're concerned, reinstating your windows boot method is generally straightforward, especially in your case where the new ubuntu install is on a different disk, but that would take away your ubuntu, so we won't do that yet.

---

### Post by mjoyce91 on 2006-09-07
k i'll try that

---

