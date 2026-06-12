---
title: "reinstalling with separate /home partition"
date: 2009-04-29
forum: General Help
---

### Post by zip_000 on 2009-04-29
Hello,

I reinstalled 9.04 yesterday after messing up some display stuff to a degree that I couldn't easily fix. I've got a separate /home partition, but I guess I missed a step in the reinstall because now the separate /home partition is just mounted as a separate partition and I have a new /home folder on the main root partition.

My question is, how do I remap the separate partition to be /home again? Also, whenever I go to the old /home partition, it asks me for my password. Now I used the same username and password for the reinstall, so that isn't an issue, just some additional information if that helps.

Thanks!

---

### Post by zvacet on 2009-04-29
```
cat /etc/fstab
```

Post it here.

---

### Post by zip_000 on 2009-04-29
I'm at work now, but I will do so this evening. Thanks!

---

### Post by zip_000 on 2009-04-29
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=fc9eb3c7-9709-4faa-808d-4f5e4f0fc037 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7e8383c8-e10d-4097-ac46-c643503efc7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by zip_000 on 2009-04-29
Alright, I think I've got it done on my own. Thanks for the help though.

I followed a guide to move the /home folder to a new partition and that worked fine even though I had data on the old home partition already.

---

### Post by fourbit on 2009-05-01
Hey ZIP!

Which guide did you use?

Thanks,

---

### Post by zvacet on 2009-05-01
You can use [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.

---

