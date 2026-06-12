---
title: "Cant view other partitions"
date: 2007-11-21
forum: Desktop Environments
---

### Post by vishi on 2007-11-21
Hi All

I have a clean install of Gutsy and everything was working fine. I was able to access all my windoze partitions (read + write). I am currently using the reiserfs for ubuntu. Now, when i boot into ubuntu, I am not able to see any of the other partitions mounted on the desktop. I am not sure what caused the issue, but I ran Gparted to get a better idea and I see that there are the yellow exclamation marks next to my other partitions. Trying to double click them yields a result which says "Unable to read the contents of this filesystem - Because of this some operations may be unavailable." 

Screenshots from Gparted are attached. Also, here's the /etc/fstab and fdisk outputs. Please help me recover my other paritions... lots of data i need to access.
Disk configuration : 80 GB + 250GB + 250GB + DVD Writer.


GParted Screen shots:
[ [IMG]http://www.imagehosting.com/out.php/i1393431_ScreenshotdevsdcGParted.png[/IMG]](http://www.imagehosting.com)[ [IMG]http://www.imagehosting.com/out.php/i1393430_ScreenshotdevsdbGParted.png[/IMG]](http://www.imagehosting.com)[ [IMG]http://www.imagehosting.com/out.php/i1393429_ScreenshotdevsdaGParted.png[/IMG]](http://www.imagehosting.com)


```

-----
FSTAB
-----

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=a5c95cf5-66ca-4ce5-81d8-2f1d5ddcb6fd /               reiserfs notail          0       1
# /dev/sda1
UUID=E6C4B046C4B01AAF /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=66DAF67DDAF64937 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=01C60EAB15D4C560 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=01C60EAB17E4B9A0 /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=8860112460111A90 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=DEB8B6F4B8B6C9F3 /media/sdb6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=FCF4C536F4C4F444 /media/sdb7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=88B4FA09B4F9FA10 /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc5
UUID=686C48466C48116C /media/sdc5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc6
UUID=74584F59584F196E /media/sdc6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=1993d921-0bc1-4e83-867e-9e41c6bcb53e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


```


:confused:
```

-----
FDISK
-----
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76f176f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431    7  HPFS/NTFS
/dev/sda2            1246        9729    68147730    5  Extended
/dev/sda5            1246        3735    20000893+   7  HPFS/NTFS
/dev/sda6            3736        6225    20000893+   7  HPFS/NTFS
/dev/sda7            6226        8715    20000893+   7  HPFS/NTFS
/dev/sda8            8716        9632     7365771    7  HPFS/NTFS
/dev/sda9            9633        9729      779121   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a2b872d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1567    12586896   af  Unknown
/dev/sdb2            1568       30401   231609105    5  Extended
/dev/sdb5            1568       12010    83883366    7  HPFS/NTFS
/dev/sdb6           12011       21200    73818643+   7  HPFS/NTFS
/dev/sdb7           21201       30401    73907001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb162c068

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10443    83883366    7  HPFS/NTFS
/dev/sdc2           10444       30401   160312635    5  Extended
/dev/sdc5           10444       20886    83883366    7  HPFS/NTFS
/dev/sdc6           20887       30401    76429206    7  HPFS/NTFS

```

```
 df -h output:

vishi@vishi-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             7.1G  3.4G  3.7G  48% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.22-14-generic/volatile


```

As you can see only the above f/s are mounted

Thanks in advance!
-Vishi

---

### Post by bingoUV on 2007-11-21
Only ntfs partitions have the exclamation mark. Do you run windows?

If yes,  did windows shutdown uncleanly, or at least it thinks it was? Can you check filesystem after booting into windows?

If not, you can do the stuff with ntfs-3g. Backup a small partition (the whole device), and mount it forcibly. 
```

sudo mount -t ntfs-3g -o force,ro /dev/sdXY /media/sdXY

```See if your stuff is present. If yes, congratulations. If not, restore the whole partition device from backup.

---

### Post by vishi on 2007-11-21
> **bingoUV said:**
> Only ntfs partitions have the exclamation mark. Do you run windows?

If yes,  did windows shutdown uncleanly, or at least it thinks it was? Can you check filesystem after booting into windows?


Well I do run windows XP and I havent shut it down forcibly. Well, I can try doing a chkdsk on windows and see if it goes well. I am at work now and Ill do this as soon as I get home. 

> 
If not, you can do the stuff with ntfs-3g. Backup a small partition (the whole device), and mount it forcibly. 
```

sudo mount -t ntfs-3g -o force,ro /dev/sdXY /media/sdXY

```See if your stuff is present. If yes, congratulations. If not, restore the whole partition device from backup.

I am a little dumb on the Linux side.. what do you mean by backing up a partition.. does it mean the same as it means on windows ? (copy all data of that partition and put it away someplace safe?)

Thanks for your suggestions.. will try em out today!

---

### Post by bingoUV on 2007-11-22
Backup a partition : If you want to backup partition /dev/sda1, which is of 10GB, find another partition which has a working file system (any) and at least 10GB free space. Suppose the free partition is mounted at /media/backup. Now
```

dd if=/dev/sda1 of=/media/backup/bkpOfsda1.img

```In the above command, use sudo if permissions are insufficient to either read from /dev/sda1 or write to /media/backup/bkpOfsda1.img. To restore, use
```

sudo dd if=/media/backup/bkpOfsda1.img of=/dev/sda1

```
 
EDIT : the target filesystem (where bkpOfsda1.img is going) should be able to take a file as large as 10GB. I guess FAT32 cannot do that ; FAT16 surely cannot do that. ext2/3, NTFS , reiser, xfs should be fine.

---

### Post by vishi on 2007-11-23
I just booted into windows once, and then back on to Ubuntu and all partitions were back! I didnt have to do anything like chkdsk or even backup my partitions. Thanks for your assistance bingoUV! 

Admins: Thread can be locked / closed

---

