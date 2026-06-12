---
title: "mounting FreeBSD disk"
date: 2008-12-10
forum: General Help
---

### Post by hirohitosan on 2008-12-10
Hi there. 
Ho can I mount in Ubuntu read & write a FreeBSD volume?
my fdisk -l output looks like:
```
fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59347   476704746   83  Linux
/dev/sda2           59348       60801    11679255    5  Extended
/dev/sda5           59348       60801    11679223+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000217fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   a5  FreeBSD

```

I want to mount and write on /dev/sdb1
it is possible
thanks

---

