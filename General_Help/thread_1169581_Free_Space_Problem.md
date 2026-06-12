---
title: "Free Space Problem"
date: 2009-05-25
forum: General Help
---

### Post by Emegs on 2009-05-25
Hello,

I started running Linux less than two days ago, so I'm probably not going to completely understand a very technical explanation.

I have my hard drive partitioned to run Windows XP and Ubuntu.  (250GB total: ~40 GB alloted to XP, a separate ~5-7GB partition, and a ~200 GB partition for Ubuntu.)

However, on my home folder it is telling me that I only have 51.8 MB of free space. (I'm thinking that with such a large partitiion, there should be a lot more free space)  I entered the command that it told me would free up space; that brought me up to 51.8 MB free space from 7.1 MB free space.

If someone could explain what's going on and how to fix the problem, it would be greatly appreciated. :)

Thanks,

~ Emegs

---

### Post by taurus on 2009-05-25
Do you have a separate partition for /home?  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
cat /etc/fstab
df -h
```
That is a lower case letter L, not number 1.

---

### Post by Emegs on 2009-05-25
> **taurus said:**
> Do you have a separate partition for /home?  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR=Blue]l[/COLOR]**
cat /etc/fstab
df -h
```That is a lower case letter L, not number 1.


When I entered: 

```
Sudo fdisk -**[COLOR=Blue]l[/COLOR]**
```

I got:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbcdfbcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4773    38339091    7  HPFS/NTFS
/dev/sda2            4774       30400   205848877+   f  W95 Ext'd (LBA)
/dev/sda5            5100        5418     2562336    e  W95 FAT16 (LBA)
/dev/sda6            5419       30400   200667883+   e  W95 FAT16 (LBA)
/dev/sda7            4774        5077     2441817   83  Linux
/dev/sda8            5078        5099      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1357     7783940    b  W95 FAT32

```



When I entered:

```
cat /etc/fstab
```

I got:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=00ad008f-c3aa-4f42-b799-6dec129736c9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e16673e3-6a64-4b32-8bcd-2a915f357011 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```



When I entered:

```
df -h
```

I got:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             2.3G  2.2G   46M  98% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  216K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  160K  501M   1% /dev
tmpfs                 501M   84K  501M   1% /dev/shm
lrm                   501M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             7.5G  6.1G  1.4G  82% /media/Ipod

```

---

### Post by taurus on 2009-05-25
> **Emegs said:**
> 
When I entered:

```
df -h
```

I got:

```
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Red"]/dev/sda7             2.3G  2.2G   46M  98% /[/COLOR]**
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  216K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  160K  501M   1% /dev
tmpfs                 501M   84K  501M   1% /dev/shm
lrm                   501M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             7.5G  6.1G  1.4G  82% /media/Ipod

```

As you can see, you only assigned 2.3GB to Ubuntu so of course, you would run out of disk space as soon as you finished installing it since the default installation would take up that much space.  

Did you pick the right partition when you installed Ubuntu?

---

### Post by Emegs on 2009-05-25
> **taurus said:**
> As you can see, you only assigned 2.3GB to Ubuntu so of course, you would run out of disk space as soon as you finished installing it since the default installation would take up that much space.  

Did you pick the right partition when you installed Ubuntu?

Ubuntu did it automatically, it asked if what it was going to do was OK though.

It gave 191 MB to (dev/sda6) or something that looked like that, and small 2-7 GB portions to (dev/sda7) and (dev/sda5) or whatever they were. (I don't recall perfectly)

I went back and tried to make a manual partitioning but I couldn't figure out how to get it to work.

---

### Post by taurus on 2009-05-25
If you want to use the manual option, you need to tell the installer which partition (/dev/sda6 if that is what you want since it has more space on it) to mount to / (root filesystem) and format it to either ext3 or ext4.  Remember, you need to mount that partition to / or it will complain about no root filesystem later when you want to continue.

---

### Post by Emegs on 2009-05-25
> **taurus said:**
> If you want to use the manual option, you need to tell the installer which partition (/dev/sda6 if that is what you want since it has more space on it) to mount to / (root filesystem) and format it to either ext3 or ext4.  Remember, you need to mount that partition to / or it will complain about no root filesystem later when you want to continue.

When I tried to use the manual option, it didn't actually let me change anything.

I'll go try again though and try mounting it to /

EDIT:

Fixed problem, I now have 175 GB space.

Thanks dude :D

---

