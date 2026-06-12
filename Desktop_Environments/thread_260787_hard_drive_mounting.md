---
title: "hard drive mounting"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-19
Hello 

I cant get my hard drive to work I am posting a file and I need some help know what to do now!

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

bswilson told me to poat this file

Thanks

---

### Post by whizbaby on 2006-09-19
This doesn't seem to be the problem. A bit more information please (whole HD setup in your computer, how did you install, did it work and then stop, exact symptoms?)!

---

### Post by Magiczero on 2006-09-19
Iget an error that says The drive is not remoutable but it is an internal drive.  It is mounted with IDE Cables.  The drive is viewable in Computer but when I click it I get that error!

The BOIS reconiges it as a drive.

Thanks

---

### Post by Magiczero on 2006-09-19
it hasnt worked

---

### Post by Magiczero on 2006-09-19
works on xp

---

### Post by whizbaby on 2006-09-19
What you say strongly suggests that your ubuntu loads > when I click  it, so your harddrive *is* working. Open a terminal and type **ls  /** to see if it's really not mounted.

---

### Post by Magiczero on 2006-09-19
This is a second 200 gig drive not my boot drive!

---

### Post by whizbaby on 2006-09-19
Lets's say your drive is an additional IDE drive and you want to mount its first partition to */media/second*, then type (to terminal):
**sudo mkdir /media/second**
then open an editor to append to your /etc/fstab:
[I]/dev/hdb1 /media/second ext3 defaults,errors=remount-ro 0 1
[/I]
then again in terminal
**mount -a**

drive should be accessible at /media/second.

---

