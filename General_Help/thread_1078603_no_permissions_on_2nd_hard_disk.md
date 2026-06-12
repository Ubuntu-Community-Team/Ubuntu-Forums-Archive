---
title: "no permissions on 2nd hard disk"
date: 2009-02-23
forum: General Help
---

### Post by fcuk112 on 2009-02-23
i don't have r/w permissions on my 2nd hard disk, can someone please advise how i should configure fstab?

sudo fdisk -l:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7f0c5d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29646   238131463+  83  Linux
/dev/sda2           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=966e2363-6412-499c-8750-b36e5fd972e1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f70af64a-9219-4f32-b387-e9f9ee326bea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/media/disk	ext3 defaults 0 2

many thanks!
frank.

---

### Post by Slim Odds on 2009-02-23
What does:```
sudo ls -l /media/disk
```say?

or even just:```
ls -l /media/disk
```

---

### Post by alexandari on 2009-02-23
are you able to do something using root on you`r 2nd hard disk or you can`t do anything at all?

---

### Post by taurus on 2009-02-23
Just change the ownership of /media/disk from root to your login name.  Then, you can write to it anytime you want without using sudo/gksudo.

```
sudo chown -R *username*:*username* /media/disk
```
Replace *username* with your login name.

---

### Post by fcuk112 on 2009-02-23
yes i can do stuff using root but not using nautilus.  ls -l /media/disk gives:

total 20
drwx------ 2 root root 16384 2008-12-04 00:44 lost+found
drwxr-xr-x 2 root root  4096 2009-02-23 18:50 Series

---

### Post by Slim Odds on 2009-02-23
> **fcuk112 said:**
> yes i can do stuff using root but not using nautilus.  ls -l /media/disk gives:

total 20
drwx------ 2 root root 16384 2008-12-04 00:44 lost+found
drwxr-xr-x 2 root root  4096 2009-02-23 18:50 Series

Do like taurus says....

---

### Post by fcuk112 on 2009-02-23
thank you very much - this has resolved the problem!

---

