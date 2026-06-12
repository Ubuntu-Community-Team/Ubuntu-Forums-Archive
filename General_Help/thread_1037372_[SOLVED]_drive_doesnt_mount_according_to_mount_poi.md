---
title: "[SOLVED] drive doesnt mount according to mount point in fstab"
date: 2009-01-11
forum: General Help
---

### Post by Azazel on 2009-01-11
I want my second drive to be used just backup. a single ext2 partition mounted at /media/backup. however it will not mount there, the only time i can get it to mount automatically it mounts to /media/disk. also my two drives, sda and sdb, reverse lables seemingly randomly. heres my fstab, fdisk -l, df -h and blkid.

```


# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   <type>  	<options>       			<dump>  <pass>
proc            				/proc           proc    	defaults        			0       0
#
# /dev/sda1
UUID=ddc3c3f3-648a-44df-a41e-ca1a81292e70 	/               ext3    	defaults,errors=remount-ro,relatime 	0       1
#
# /dev/sda2
UUID=01C96E054BE1C970				/media/windows	ntfs-3g		defaults,locale=en_US.utf8		0	0
#
# /dev/sda5
UUID=f9af1ba1-8eb4-4bad-8250-621273233b94 	none            swap    	sw              			0       0
#
# /dev/sda6
UUID=362b7d5e-e18e-4b7d-918b-074adba3f99d	/home/kory   	ext2    	defaults,nodev,nosuid,relatime 		0       1
#
# /dev/sdb1
#UUID=df554ff6-74fe-4451-b6cd-86b16dd54bf0 	/media/backup	ext2		defaults				0	1
#
/dev/scd0       				/media/cdrom0   udf,iso9660 	user,noauto     			0       0
#
#/dev/fd0        				/media/floppy0  auto    	rw,user,noauto  			0       0
#
#/home/kory/Morrowind/2-Bloodmoon.iso		/media/cdromv1	udf,iso9660	user,noauto,exec,loop			0	0

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c6abe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ec6dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3916    31455238+  83  Linux
/dev/sdb2   *        3917       15665    94373842+   7  HPFS/NTFS
/dev/sdb3           15666       60801   362554920    f  W95 Ext'd (LBA)
/dev/sdb5           15666       16025     2891668+  82  Linux swap / Solaris
/dev/sdb6           16026       60801   359663188+  83  Linux

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              30G  4.7G   24G  17% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  100K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  104K 1012M   1% /dev/shm
/dev/sdb2              91G   28G   63G  31% /media/windows
/dev/sdb6             338G   74G  254G  23% /home/kory
/dev/scd0             4.2G  4.2G     0 100% /media/cdrom0
/dev/sda1             232G   60M  220G   1% /media/disk

/dev/sda1: UUID="df554ff6-74fe-4451-b6cd-86b16dd54bf0" TYPE="ext2" 
/dev/sdb1: UUID="ddc3c3f3-648a-44df-a41e-ca1a81292e70" TYPE="ext3" 
/dev/sdb2: UUID="01C96E054BE1C970" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="f9af1ba1-8eb4-4bad-8250-621273233b94" 
/dev/sdb6: UUID="362b7d5e-e18e-4b7d-918b-074adba3f99d" TYPE="ext2" 


```

as far as i can see there is nothing wrong with my fstab, so i have no clue whats happening. thanks in advance for any help you might be able to offer me!

---

### Post by electrogeist on 2009-01-11
```


#UUID=df554ff6-74fe-4451-b6cd-86b16dd54bf0 	/media/backup	ext2		defaults				0	1

```


did you really mean to comment out this line ?

---

### Post by Azazel on 2009-01-11
omg i feel like an idiot! i guess it just needed a new set of eyes. thanks for your help!

---

