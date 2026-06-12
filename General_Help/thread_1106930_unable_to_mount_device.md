---
title: "unable to mount device"
date: 2009-03-26
forum: General Help
---

### Post by katnalie on 2009-03-26
I reinstalled Ubuntu on my computer and i am unable to see all my devicesI have get the following message :
$Logfile indicates unclean shutdown (0,0).Failed to mount /Mount is denied because NTFS is marked to be in use

I tried to mount them manually with this comand 
 sudo mount /dev/sda1
 and i get this
 mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by katnalie on 2009-03-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e32f8bbb-7e31-4d42-ae5e-823f4495f886 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f62fcd12-a83d-432e-acf1-4bad1b5878b2 none            swap    sw              0       0
# /dev/sdb5
UUID=8e0ec26f-0e1e-4f57-a64d-94027be0bc6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


my fstab looks like this and my partitions looks like

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x895c895c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8925        9306     3068415    f  W95 Ext'd (LBA)
/dev/sda3            9307       19457    81537907+  83  Linux
/dev/sda5            8925        9306     3068383+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe65be65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fe44fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3952    31744408+   7  HPFS/NTFS
/dev/sdc2            3953       30401   212451592+   5  Extended
/dev/sdc5            3953        8922    39921493+  83  Linux
/dev/sdc6            9242       30401   169967668+   7  HPFS/NTFS
/dev/sdc7            8923        9241     2562336   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by coffeecat on 2009-03-26
This is your problem. Windows (I presume on sda1) suffered an unclean shutdown.

> **katnalie said:**
> $Logfile indicates unclean shutdown (0,0).Failed to mount /Mount is denied because NTFS is marked to be in use

The filesystem needs repairing. It's a safety feature. Ubuntu doesn't want to mount a possibly damaged filesystem. But once repaired, you should be able to automount an NTFS partition simply by going to Places in the main menu.

Try booting up Windows. If it boots, do a 'chkdsk' from a command window or somewhere in the program lists is a utility for repairing the filesystem. If Windows won't boot up normally, try to boot up in safe mode, and then repair your C: partition.

There is a way of force mounting an NTFS partition from Linux, but it is much better to let Windows repair the filesystem.

---

