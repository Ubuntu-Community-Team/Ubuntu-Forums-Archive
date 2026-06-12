---
title: "FAT32 formatted slave"
date: 2005-12-11
forum: General Help
---

### Post by maccom on 2005-12-11
i run both windows xp and breezy, 
in installation i put breezy on my slave and gave 30gb of space to be fat32 formatted, 
when i booted into linux i couldn't see the space.
so i booted into windows, which could see it, but it was not formatted so i formatted it using windows as fat32 (no mount point??) 
only windows NOT breezy can now see this space.

what do i need to do so breezy and windows can read alongside each other?

---

### Post by aysiu on 2005-12-11
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

It assumes your FAT partition is at /dev/hda1. It's probably /dev/hdb2, though. To be sure, check out the output of this command ```
sudo fdisk -l
```

---

### Post by maccom on 2005-12-11
sorry it was my bad...
i run linux off of my slave /dev/hdd1 and i made 30 gb of my 40 gb hdd1 FAT

would this still work??


.... my internet connection is only in windows as i use a USB modem, im getting a router soon!

---

### Post by aysiu on 2005-12-11
[QUOTE=maccom]sorry it was my bad...
i run linux off of my slave /dev/hdd1 and i made 30 gb of my 40 gb hdd1 FAT

would this still work??[/QUOTE] Yes. Please follow the directions I gave you. Let me know if you don't know where to put those commands.

---

### Post by mherring on 2005-12-11
[QUOTE=maccom]sorry it was my bad...
i run linux off of my slave /dev/hdd1 and i made 30 gb of my 40 gb hdd1 FAT

would this still work??[/QUOTE]

something is wrong here---hdd means the fourth drive on the IDE bus.  hdd1 means the first partition of hdd.
You can't have Linux on hdd1 and also have it be a FAT partition.

run fdisk on all your drives:  fdisk /dev/hdX, then p to print the partition table
(X=a, b, c, d, e---etc)

[QUOTE=
.... my internet connection is only in windows as i use a USB modem, im getting a router soon![/QUOTE]

What has this got to do with the question????????

---

