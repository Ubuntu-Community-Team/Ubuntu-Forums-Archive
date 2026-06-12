---
title: "Installation Problems"
date: 2005-12-18
forum: General Help
---

### Post by scole on 2005-12-18
I recently got the 2 disk live and install cd set off a friend. I have used the live cd on my dell and love it. But i want to install ubuntu onto my older pc. I had problems booting from cd although i fixed that with a boot disk that allows me to select what i want to boot from. i can get the setup to run fine until it opens the partioner. it then procedes to crash with a message at the bottom that says feature not implemented. it refuses to open up the partioner. and it will go no further. what should i do? i have put a stat sheet for my comp below

--My Computer--
P II 333mhz
64 MB RAM
6.5 gb HDD with WIN XP Home installed
16 mb AGP ATI all-in-wonder
ISA Sound Blaster AWE64 card
old hitachi dvd drive
Iomega cd-r drive
floppy drive

---

### Post by thalliwell on 2005-12-18
Seems like a hard disk issue.

If you can do without winxp then I would Reformat the hard drive as fat32 and try to install.

---

### Post by scole on 2005-12-18
The HDD is formatted in FAT32. I made sure after i put xp on. and i just reformatted yesterday

---

### Post by tuxy on 2005-12-18
Run the Ubuntu or any other linux "live CD" distro you have. Partition the harddrive properly with "cfdisk". Type in cfdisk /dev/hda or /dev/hdb whatever partition you have. You can change the file system type in the partitioned space my typing
mkfs.ext3 /dev/hda or /hdb.

It will much easier this way. Let me how it went :)

---

### Post by zoiks on 2005-12-19
64MB may be too thin on RAM to run ubuntu unless it's for a simple no-graphics fileserver or something.  Most modern Linux desktops need 128MB or more.  If you still want to run on 64 megs you should try a lighter-weight window manager.  I don't know what ubuntu allows, but you could check for icewm, xfce, and the like.

---

### Post by tuxy on 2005-12-19
If that's the case then go for Puppy Linux live. It fits on a 64MB USB flash drive-it is lightning fast. The whole o/s runs from the RAM instead of bothering the live CD like in other live CD's.

In fact, I run my Debian Sarge on 96MB RAM with 3GB hard drive.

---

### Post by newuser111 on 2005-12-19
or just use xubuntu, it works pretty good

[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

---

### Post by scole on 2005-12-20
Well i got it working. I partioned some space out ahead of time with bootit. When i got into setup all went well and it installed fine thanks

---

