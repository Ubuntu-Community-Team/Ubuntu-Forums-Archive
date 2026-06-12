---
title: "dd_rhelp"
date: 2009-05-05
forum: General Help
---

### Post by iecltd on 2009-05-05
I have what I suspect is a hard drive fauly although it occurred 48hrs after upgrading to 9.04. The drive appear correct in fdisk but shows as unknown file type in GParted. I wanted to try to backup the data and duly installed dd_rhelp. It installed without any errors but when I try to run it it tell me it cannot open the .img file. 
the command I used is "sudo dd_rhelp /dev/sdb1 /dev/sdd1/backup.img"
In case the drive being copied was the problem I tried another partition and still get the same error message.
Any ideas what may be causing this?

Rodney Rundstrom

---

### Post by sefs on 2009-07-09
This is a bit late but  should not the second argument be to a mounted location...


so for instance your sdd1 partition would be mounted to for example /media/disk so the command would look like.

```

sudo ./dd_rhelp /dev/sdb1 /media/disk/backup.img

```

---

