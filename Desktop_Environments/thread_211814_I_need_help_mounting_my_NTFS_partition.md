---
title: "I need help mounting my NTFS partition"
date: 2006-07-08
forum: Desktop Environments
---

### Post by ekuliak on 2006-07-08
I installed a new hard drive recently, a 320GB drive I formatted to NTFS.

How do I mount it?


/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


```



Results of fdisk -l:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       13027    94156965    f  W95 Ext'd (LBA)
/dev/sda5            1306        1567     2104483+  82  Linux swap / Solaris
/dev/sda6            1568       13027    92052418+  83  Linux

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6483    52074666    7  HPFS/NTFS
/dev/sdb2            6484        9730    26081527+   f  W95 Ext'd (LBA)
/dev/sdb5            6484        9730    26081496    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sdc5               2       38913   312560608+   7  HPFS/NTFS
ekuliak@ekuliak-desktop:~$ cd /etc
ekuliak@ekuliak-desktop:/etc$ sudo gedit fstab
ekuliak@ekuliak-desktop:/etc$ sudo mount -a
mount: mount point /media/sdc1 does not exist
mount: mount point /media/sdc5 does not exist
ekuliak@ekuliak-desktop:/etc$ sudo gedit fstab
ekuliak@ekuliak-desktop:/etc$ clear

ekuliak@ekuliak-desktop:/etc$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       13027    94156965    f  W95 Ext'd (LBA)
/dev/sda5            1306        1567     2104483+  82  Linux swap / Solaris
/dev/sda6            1568       13027    92052418+  83  Linux

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6483    52074666    7  HPFS/NTFS
/dev/sdb2            6484        9730    26081527+   f  W95 Ext'd (LBA)
/dev/sdb5            6484        9730    26081496    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sdc5               2       38913   312560608+   7  HPFS/NTFS


```

I believe it is that sdc5 that I want to mount.

I don't care about write access, I just want read access for all users.  I don't really care what it is mounted as, for simplicity's sake, I'll go with /media/sdc5 as the mount point.

Hopefully that is enough info ^_^


Thanks

---

### Post by aysiu on 2006-07-08
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

---

### Post by Appolusionist on 2006-07-08
> **ekuliak said:**
> I installed a new hard drive recently, a 320GB drive I formatted to NTFS.

How do I mount it?


/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


```



Results of fdisk -l:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       13027    94156965    f  W95 Ext'd (LBA)
/dev/sda5            1306        1567     2104483+  82  Linux swap / Solaris
/dev/sda6            1568       13027    92052418+  83  Linux

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6483    52074666    7  HPFS/NTFS
/dev/sdb2            6484        9730    26081527+   f  W95 Ext'd (LBA)
/dev/sdb5            6484        9730    26081496    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sdc5               2       38913   312560608+   7  HPFS/NTFS
ekuliak@ekuliak-desktop:~$ cd /etc
ekuliak@ekuliak-desktop:/etc$ sudo gedit fstab
ekuliak@ekuliak-desktop:/etc$ sudo mount -a
mount: mount point /media/sdc1 does not exist
mount: mount point /media/sdc5 does not exist
ekuliak@ekuliak-desktop:/etc$ sudo gedit fstab
ekuliak@ekuliak-desktop:/etc$ clear

ekuliak@ekuliak-desktop:/etc$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       13027    94156965    f  W95 Ext'd (LBA)
/dev/sda5            1306        1567     2104483+  82  Linux swap / Solaris
/dev/sda6            1568       13027    92052418+  83  Linux

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6483    52074666    7  HPFS/NTFS
/dev/sdb2            6484        9730    26081527+   f  W95 Ext'd (LBA)
/dev/sdb5            6484        9730    26081496    b  W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sdc5               2       38913   312560608+   7  HPFS/NTFS


```

I believe it is that sdc5 that I want to mount.

I don't care about write access, I just want read access for all users.  I don't really care what it is mounted as, for simplicity's sake, I'll go with /media/sdc5 as the mount point.

Hopefully that is enough info ^_^


Thanks

Check out this link:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

---

### Post by ekuliak on 2006-07-09
](*,)  Thanks, using the link appolusionist posted ([found here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")), I saw what I was doing wrong.  XD

I needed to make the directory first.

So, using that, in the terminal I typed:
```

sudo mkdir /media/sdc5
sudo gedit /etc/fstab
```

then when gedit opened the file to edit I added the following at the end of it:
```

/dev/sdc5    	/media/sdc5 	ntfs 	nls=utf8,umask=0222 0    0
```

And now I can read from that drive  :D 

Thanks, and hopefully this post can help someone in the future (and also help me remember what I did for future reference)  ^_^

---

