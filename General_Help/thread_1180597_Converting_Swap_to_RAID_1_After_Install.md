---
title: "Converting Swap to RAID 1 After Install"
date: 2009-06-07
forum: General Help
---

### Post by scotbuff on 2009-06-07
So a while ago I installed my Ubuntu 9.04 system with RAID 1, it has been working great.  It dawned on me that I had forgotten to setup Swap for RAID.  Is there anyway to do this after the fact?  Here is my current fstab.  Thanks in advance.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=011f92d3-7f74-4f7b-80f9-7f8ada90f695 /               ext3    relatime,errors=remount-ro,usrquota,grpquota 0       1
# /dev/sda5
UUID=f2b68d06-3f5c-41a1-9571-296d13be523f none            swap    sw              0       0
# /dev/sdb5
UUID=075a32b1-6b45-49eb-a3ed-9b0e183a6430 none            swap    sw              0       0
```

---

### Post by scotbuff on 2009-06-07
bump...:popcorn:

---

