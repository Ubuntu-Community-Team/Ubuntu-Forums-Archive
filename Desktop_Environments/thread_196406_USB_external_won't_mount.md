---
title: "USB external won't mount"
date: 2006-06-14
forum: Desktop Environments
---

### Post by WelterPelter on 2006-06-14
Hi. I had this drive working fine before. One of the Dapper upgrades made it unable to mount, however. When I try to mount it, I get this friendly message: 

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, 
       missing codepage or other error 
       in some cases useful info is found in syslog - try 
       dmesg | tail  or so

```

Here is the fdisk -l output:

```
wp@wp:~$ sudo fdisk -l /dev/sdb
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2385    19157481   83  Linux
/dev/sdb2            2386        2491      851445    5  Extended
/dev/sdb5   ?       43204       95319   418614264+  12  Compaq diagnostics

```

Would love to get this drive mounting again. There are some files on that cannot be replaced. Thanks.

---

### Post by WelterPelter on 2006-06-14
*bump* Anybody? I've looked at most of the other threads about this issue. None of them have helped so far. Can somebody hold my hand through this process?

---

