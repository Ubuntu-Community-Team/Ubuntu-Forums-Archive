---
title: "add usb flash drive to bootloader"
date: 2009-02-02
forum: General Help
---

### Post by sammydadams on 2009-02-02
Here's the deal.
I have an external usb hard drive and i would like to keep a copy of linux on my flash drive but if i enable booting from the usb in my bios, everytime i turn on my computer with the harddrive attached, it takes forever to start cause its checking that one for bootable info....is there anyway that anyone knows of to add the usb drive to the existing grub on my internal hdd so that it simply asks?...

thanks

---

### Post by caljohnsmith on 2009-02-03
How about on start up when you get the Grub menu, press "c" to get the Grub CLI, and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
The first command should show your HDD's size and partitions, and the second command will hopefully show your USB drive's size and partitions. If it is clear that (hd1) is indeed your USB drive, you could add it as a boot option to your menu.lst by first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add:
```
title USB drive
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Or if the geometry command results are unclear, please let me know their output, and also please post:
```
sudo fdisk -lu
```
With your USB drive connected. We can work from there if necessary.

---

### Post by sammydadams on 2009-02-03
thanks for the quick response...i'll try this in the next couple of days:)

---

