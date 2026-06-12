---
title: "Mounting partition problem"
date: 2006-04-22
forum: Desktop Environments
---

### Post by nelson2006 on 2006-04-22
[SIZE="2"]Hello everyone :-D ! I would like to say that I'm new in this world of linux and loving it everyday of it. Recently I downloaded Ubuntu Dapper Drake Flight 6 on my Toshiba Satellite A105-S2712 and then upgraded to the Beta Version and let me tell you all I am very pleased of how it looks, very smooth 8) ! Ok, here's where my problem started :( . I mounted my fat32 partition of windows xp to my media folder, ok everything swell to now, but when I reboot what is my surprise, THE PARTITION DISAPPEARES ](*,) !!! Please I would like a liitle help here. If you can explain it to me the easiest way possible, remember I'm brand new here :lol: . Thank you.[/SIZE]

---

### Post by Jose Catre-Vandis on 2006-04-22
A quick guess would be that you manually mounted your drive, but didn't go the extra mile and edit your fstab file to ensure it came up after reboot?

Go [here]("http://ubuntuguide.org/#automountfat"), and follow instructions.

HTH

---

### Post by nelson2006 on 2006-04-22
[SIZE="2"]Ok, after doing:

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

this was the results:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


Here I don't understand. ](*,) [/SIZE]

---

### Post by Ramses de Norre on 2006-04-22
Add a line ```
/dev/hdxx       /media/xx  vfat iocharset=utf8,umask=0000 0 0

```
And change the xx's to the apropriate values.

---

### Post by nelson2006 on 2006-04-22
[SIZE="2"]Perfect :-D ! Thanks a lot amigos, I appreciate all the the help you guys gave me =D>.[/SIZE]

---

