---
title: "Problem with Mondo.... Mondo experts wanted"
date: 2009-01-03
forum: General Help
---

### Post by sr_guy on 2009-01-03
When I try to run mondo to create a backup it scans all the folders, and after about 2% into the backup process of creating an iso it stops and gives a error that it believes the partition is a Winxp partion. I'm running ubuntu only on the master hardrive. When I installed ubuntu I told the installation to use the "whole" disk rather then split it up into two partitions. Is that causing an issue? If I reinstall and allow it to create two partitions will I only need to backup the smaller of the two partitions? Here is my current partition setup:


root@kg:/home/kg# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051927

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux <==== ubuntu
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris


This is the error I am receiving:

I think you have a Windows 9x partition.
Please install ms-sys just in case.
Done.

---

