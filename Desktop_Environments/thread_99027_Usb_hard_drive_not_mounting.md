---
title: "Usb hard drive not mounting"
date: 2005-12-04
forum: Desktop Environments
---

### Post by indusbay on 2005-12-04
HI,
I am a total noob, and i just installed kubuntu. I have tried ubuntu before for a small while, but I had problems with wifi. Kubuntu dapper is good. 
I am trying to mount a Western digital passport external hdd, and KDE shows an icon on the desktop, however, when i click on it, it says the filesystem is unknown. the usb drive is fat32. please help.
thanks in advance.

---

### Post by aysiu on 2005-12-04
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat) may help. It assumes your drive is /dev/hda1, but it's probably /dev/sda1. To be sure, look at the output of ```
sudo fdisk -l
```

---

### Post by LoclynGrey on 2005-12-05
i got the same problem but with a Fujitsu 60GB fat 32 drive + ubuntu 5.10 except I dont get the any icons show on the desktop. Still working on it.

But following the advice above in the previous posts this worked a treat. :) :)

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

Cheers

---

