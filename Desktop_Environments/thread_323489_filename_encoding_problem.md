---
title: "filename encoding problem"
date: 2006-12-22
forum: Desktop Environments
---

### Post by fantasmino on 2006-12-22
Hi guys!
**Scenario:** single pc, dafault OS Ubuntu 6.10, secondary OS Win XP, all partition in ext3 apart windows that runs on NTFS.
**Problem:** when switching from-to ubuntu-windows, some character appears in a very bad way, as ? or other ways.

I read a lot of threads about this problem, I understand that the problem is in the UTF-8 and CP850. Now I can read well character in ubuntu if I convert them in utf-8, but when I switch to win I read the same character very bad: I correct them, but when I switch to ubuntu, I need to convert them in utf-8 again to read them correctly...](*,) 

**My question:** How can I do for use the same charset in ubuntu and win xp? I use some files both in ubuntu and in xp and I switch between this two OS, and I need to solve this problem.

Anyone can help me?
Thx guys, I hope in a solution...

I paste my fstab, may be helpful? (files with problems are on sdc1, but I think in other partition, too. I'll make some tests for this)
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=62baf628-b01d-47e5-9d1e-127d1adf4af1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
/dev/sda1    /media/Eva    ntfs-3g    silent,umask=0,locale=it_IT.utf8,no_def_opts,allow_other 0 0
# /dev/sdb1
/dev/sdb1    /media/Exter    ext3    defaults        0       2
# /dev/sdc1
/dev/sdc1    /media/Linux    ext3    defaults        0       2
# /dev/sda3
UUID=1479f855-68d8-41e8-9271-bfd1b6a54e68 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by fantasmino on 2006-12-22
Someone can help me?
I'm sure that I'm not the only one with this problem...:-k

---

### Post by fantasmino on 2006-12-26
Please help!
Or I must think that what I'm asking for it is really impossible to do? :-k  
Help me!
Please!

---

### Post by GrumpyBob on 2006-12-26
I have to confess that I'm unclear what your actual problem is...perhaps it is connected with the fonts you have installed - have you installed the msttfcorefonts?

Robert

---

### Post by gantengx on 2007-10-13
I'm running into the same problem too... So far can't find any solution yet... :(

---

