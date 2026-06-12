---
title: "problem adding windows to grub"
date: 2006-08-31
forum: Desktop Environments
---

### Post by rkakkar on 2006-08-31
Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         382     3068383+  83  Linux

That's my ubuntu partition

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         637     5116671    7  HPFS/NTFS

That's my windows partition

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP
rootnoverify    (hd2,0)
savedefault
makeactive
chainloader     +1


That's my grub menu.lst. However when I try to boot windows, it says that the selected drive does not exist! :(

Also, grub gives me only 2 seconds to press 'Esc' in order to go into the grub menu and then starts loading the default menu. How can I change that to the handling where grub shows me the menu and gives me around 8 seconds or so to make the choice and if I don't it would then boot up the default OS?

---

### Post by craig552 on 2006-08-31
Looks like you've got windows on **hdc1** (line 7) and rootnoverify pointing to (**hd2**,0)
You should change these so they match. 
hdc1 = (hd3,0)
hdb1 = (hd2,0)

All Grub's setting are stored in the file /boot/grub/menu.lst.
Before editing, backup with
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` 
then edit it using
```
sudo gedit /boot/grub/menu.lst
```
To change the timeout adjust the line
```
timeout     2
```
You should see the setting for displaying the grub menu in this file too. 
I can't remember what it is, and I've deleted it from mine.
You can comment it out by putting a '#' at the start of the line.

---

