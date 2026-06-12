---
title: "Automount NTFS partitions stopped working"
date: 2008-12-31
forum: General Help
---

### Post by vampire666eng on 2008-12-31
Hi there.
I updated my ubuntu 8.10 with the "Update Manager" and after I re-booted my drives (internal hard disk) where not automounted (no icons on the desktop).

I know that I should add some line in the fstab but I don't have the slightest idea...I checked the forums but wasn't able to find anything.

This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc6
UUID=6dfe30d0-866a-45c7-b544-e4f45f4a44d0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=53c407f5-fd01-0236-a511-628305dba820 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb1 	/media/WindowsXP 	ntfs defaults 0 1
/dev/sdc5 	/media/Downloads 	ntfs defaults 0 1
/dev/sda1 	/media/Programmi 	ntfs defaults 0 1
/dev/sdb5 	/media/Games 		ntfs defaults 0 1

```

I'm pretty sure that I need to add/remove something after "ntfs" to tell ubuntu to automount the drives...not sure of what command though.

Thanks for your help.

---

### Post by prshah on 2008-12-31
> **vampire666eng said:**
> This is my fstab:
```

/dev/sdb1 	/media/WindowsXP 	ntfs defaults 0 1
/dev/sdc5 	/media/Downloads 	ntfs defaults 0 1
/dev/sda1 	/media/Programmi 	ntfs defaults 0 1
/dev/sdb5 	/media/Games 		ntfs defaults 0 1

```

Your fstab looks fine. Using "defaults" automatically uses the "auto" keyword.

Can we have a look at your ```
sudo fdisk -l
sudo blkid
ls -l /media
```

Do icons appear for each drive in "Places->Computer"?

---

### Post by wd5gnr on 2008-12-31
If your NTFS shutdown unclean it will refuse to mount until Windows blesses it or you force a mount. 

If you issue:

sudo mount /media/WindowsXP

from a terminal what does it say?

---

### Post by vampire666eng on 2008-12-31
> **prshah said:**
> Your fstab looks fine. Using "defaults" automatically uses the "auto" keyword.

Can we have a look at your ```
sudo fdisk -l
sudo blkid
ls -l /media
```

Do icons appear for each drive in "Places->Computer"?
That is really strange. I was in Windows XP when I read your reply, so in order to post what you asked I booted ubuntu, then I saw a line with the red text "fail", then once ubuntu finished booting....the drives where automounted. I didn't touch a thing...

I'll post what you asked anyway (maybe there's still something wrong)?
sudo fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a8ae86c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6529    52444161    7  HPFS/NTFS
/dev/sda2            6530        9079    20482875    f  W95 Ext'd (LBA)
/dev/sda3            9080        9732     5245222+  83  Linux
/dev/sda5            8820        9079     2088418+  82  Linux swap / Solaris
/dev/sda6            6530        8819    18394362   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a850a85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2296    18442588+   7  HPFS/NTFS
/dev/sdb2            2297       14593    98775652+   f  W95 Ext'd (LBA)
/dev/sdb5            2297       14593    98775621    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xefc087f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2      775221   390710880    f  W95 Ext'd (LBA)
/dev/sdc5               2      775221   390710848+   7  HPFS/NTFS

```
sudo blkid:
```

/dev/sda1: UUID="E0ECE3E5ECE3B3C6" LABEL="Programmi (Maxtor)" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="53c407f5-fd01-0236-a511-628305dba820" 
/dev/sdb5: UUID="7A88AFB688AF6EF7" LABEL="Games (Seagate)" TYPE="ntfs" 
/dev/sdc5: UUID="60BCECE3BCECB526" LABEL="Downloads (Hitachi)" TYPE="ntfs" 
/dev/sda3: UUID="5b3dee58-23fc-4858-ba2b-6d6f8e32d911" TYPE="ext2" 
/dev/sda6: UUID="6dfe30d0-866a-45c7-b544-e4f45f4a44d0" TYPE="ext3" 
/dev/sdb1: UUID="34741DE0741DA5A0" LABEL="WindowsXP (Seagate)" TYPE="ntfs"
```
ls -l /media:
```

total 80
lrwxrwxrwx 1 root root     6 2008-11-01 20:38 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-11-01 20:38 cdrom0
drwxr-xr-x 2 root root  4096 2008-11-01 20:38 cdrom1
drwxr-xr-x 2 root root  4096 2008-11-01 20:38 cdrom2
drwxrwxrwx 1 root root 28672 2008-12-31 00:38 Downloads
drwxrwxrwx 1 root root 24576 2008-12-31 00:38 Games
drwxr-xr-x 2 root root  4096 2008-11-05 22:02 Programmi
drwxrwxrwx 1 root root 12288 2008-12-31 01:28 WindowsXP

```

Is there a way I can see what was that red "fail" about? Maybe it's related, I don't know...

---

### Post by vampire666eng on 2008-12-31
> **wd5gnr said:**
> If your NTFS shutdown unclean it will refuse to mount until Windows blesses it or you force a mount. 

If you issue:

sudo mount /media/WindowsXP

from a terminal what does it say?

That makes a lot of sense considering what happened (look at my previous post)....;)

Thanks for the reply to both of you. :)

---

### Post by prshah on 2008-12-31
> **vampire666eng said:**
> 
I'll post what you asked anyway (maybe there's still something wrong)?


> **wd5gnr said:**
> If your NTFS shutdown unclean it will refuse to mount until Windows blesses it or you force a mount. 


wd5gnr is right, of course, that is the most common reason. (Note to self; when you hear hooves, think horses, not zebras). 

Everything else looks fine, but just a suggestion: You should use UUIDs rather than device IDs in the fstab. /dev/sd?? device IDs can change, even if you don't change the hard disks physically (for example with a BIOS change, or adding a new HDD, so forth). The UUIDs for each partition are listed in the "blkid" command output. Something to think about...

---

