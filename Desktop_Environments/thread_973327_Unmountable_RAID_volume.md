---
title: "Unmountable RAID volume"
date: 2008-11-06
forum: Desktop Environments
---

### Post by s_raiguel on 2008-11-06
I can't seem to mount my RAID 0 volume, running under Intel's BIOS-based AHCI RAID manager. Here's what happened: I freed up an extra harddrive (not a RAID volume) in my Dell, and decided to install Ubuntu 8.1 on it, with XP residing on the primary, RAID drive. Since I'd had had problems before installing on a second hard drive that had resulted in neither Windows nor Unbuntu booting, I decided to unplug both RAID member drives so that the Ubuntu installation couldn't try any monkey business with them while installing. When all was done, both Windows and Ubuntu booted nicely by selecting the boot drive from the BIOS boot options. The problem was, the Ubuntu installation didn't see and would not mount the RAID NTFS volume, so that I can share data between the operating systems. The RAID volume is apparently active, since FDISK -l shows: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       60395   485074642+   7  HPFS/NTFS
/dev/sda3           60396       60787     3148740   db  CP/M / CTOS / ...


which are all partitions on the RAIDed drive. Also, dmraid -r gives 

/dev/sdb: isw, "isw_diiiejfeia", GROUP, ok, 488281248 sectors, data@ 0
/dev/sda: isw, "isw_diiiejfeia", GROUP, ok, 488281248 sectors, data@ 0

Where "isw" indicates Intel software RAID, and 488 gig is about the size of half-terabyte drive. Also, dmraid -ay says that the array is already active. 

However, there's no mention of /dev/sda* (the main, NTFS partition) in /etc/fstab.conf, which has only these entries

# Entry for /dev/sdc1 :
UUID=419a3127-33b3-41ee-b346-1852839e0ac2 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=752cc207-4020-484d-bf62-a37c1026362e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

So, I take it that I need to add a reference to /dev/sda2 to fstab to get the NTFS RAID volume to mount, but how do I get an "UUID" for it, and what parameters should I give? Is there some utility to automatically add volumes to fstab without having to edit it manually?

---

