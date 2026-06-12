---
title: "Mounted disk don't automont after reboot"
date: 2006-08-04
forum: Desktop Environments
---

### Post by aba3k on 2006-08-04
Hi all,

Recently i put a new HD in my ubuntu 6.06. The drive was recognized and all was ok. I can mount they whithout problems, but after a reboot they don't automont.

The drive in fdisk:
/dev/hdc1               1        9729    78148161   83  Linux

+++++++++++++++++++++++++++++++++++++++
fstab:
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/hda4       /files          ext3    defaults        0       2
/dev/hdc1       /files2         ext3    defautls        0       2
/dev/hda2       /home           ext3    defaults,usrquota,grpquota        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

---

### Post by ciscosurfer on 2006-08-04
Did you add a drive to linux that was formatted/partitioned for linux or did you add a drive that was formatted/partitioned for windows?  If it's the latter and it's XP, you need an NTFS rule added to your fstab.  If it's older than XP, you need a VFAT line added.  

What's your setup (how are you using this drive?)

---

### Post by ifokkema on 2006-08-04
You got a typo:
```
/dev/hdc1 /files2 ext3 defautls 0 2
```
SHOULD BE:
```
/dev/hdc1 /files2 ext3 defaults 0 2
```
:)

---

### Post by ciscosurfer on 2006-08-04
@ifokkema

Good eye my friend!

---

### Post by aba3k on 2006-08-04
My mistake, thank you guys. ;)

---

