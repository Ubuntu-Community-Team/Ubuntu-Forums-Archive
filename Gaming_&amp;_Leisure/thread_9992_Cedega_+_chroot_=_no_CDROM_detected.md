---
title: "Cedega + chroot = no CDROM detected"
date: 2005-01-03
forum: Gaming &amp; Leisure
---

### Post by Dylanby on 2005-01-03
I posted this at the Transgaming forum also.
I'm posting it here too because I'm an impatient SOB. :D 

I'm running Ubuntu AMD64 with a 32bit chroot.
I've successfully downloaded & installed Point2Play & Cedega into the chroot.

Now I want to install Half-Life 2, but I can't get Point2Play to see my DVDRW (cdrom0).

I'm not sure whether I screwed up on that part of the the chroot so here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs defaults        0       1
/dev/hda4       /home           reiserfs defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/home /var/chroot/home none bind 0 0
/tmp /var/chroot/tmp none bind 0 0
/proc /var/chroot/proc proc defaults 0 0
/media/cdrom0 /var/chroot/media/cdrom0 none bind 0 0
``` 

All of Point2Play's system tests were ok except for the cd/dvd one. When I insert the HL2 DVD Ubuntu detects it & opens Nautilus. Not so with P2P.

Again, I'm not sure if this is a chroot thing or a permissions thing or what.

---

### Post by daniels on 2005-01-03
You need to bind-mount /dev into the chroot, not /media/cdrom0.

---

### Post by Dylanby on 2005-01-04
I'm somewhat new to Linux so your advice is lost on me (my fault, not yours).
I already have a /var/chroot/dev.

---

### Post by dmatrix on 2005-01-04
Anytime you insert a cd and it is automounted you will also need to mount the cdrom in the chroot. When done with the cd you must first umount it from the chroot then normally umount it. This can cause some issues and I have just copied the cd(s) to my hard drive first before installing or I use one of the Loki installers from here:

[http://liflg.org/](http://liflg.org/)

---

