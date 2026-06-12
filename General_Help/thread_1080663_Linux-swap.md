---
title: "Linux-swap"
date: 2009-02-25
forum: General Help
---

### Post by BiynaYahu on 2009-02-25
I've added a new swap to my Laptop.  I had 20GB of free space.  So, I moved my partitions to the end of the drive, grew my /home, and left 4GB between my /boot, and /root.  I of course set the 4GB to linux-swap.  Now I want to know how to cause my system to load that swap on boot.  Thank you in advance.

---

### Post by taurus on 2009-02-25
You need to add an entry in /etc/fstab for that swap partition.  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -m
```

---

### Post by BiynaYahu on 2009-02-25
I'm currently in the process of re-partitioning without backing up my data.  So, as soon as it is finished, if I still have data left, I will do just that.  Also, I am running from a LiveCD, and can't mount my partitions properly.  See here: [http://ubuntuforums.org/showthread.php?t=1080608](http://ubuntuforums.org/showthread.php?t=1080608)

---

### Post by jimmyhacker on 2009-02-25
open terminal and add in /etc/rc.d/rc.local this line:
[PHP]swapon -a[/PHP]

---

### Post by BiynaYahu on 2009-02-25
biynayahu@biynayahu-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+  83  Linux
/dev/sda2             539        2405    14996677+  83  Linux
/dev/sda3            2406       14593    97900110   83  Linux
/dev/sda4              17         538     4192965   82  Linux swap / Solaris

Partition table entries are not in disk order

biynayahu@biynayahu-laptop:~$ sudo blkid

/dev/sda1: UUID="5b9f8393-de40-4fee-9c50-d6b140eb4395" TYPE="ext2" 
/dev/sda2: UUID="78cb62eb-3101-464a-b3e2-46773c2194af" TYPE="jfs" 
/dev/sda3: UUID="7d4cc23a-79c7-4156-980a-3e948c0d6a83" TYPE="jfs" 
/dev/sda4: UUID="f2f28c8b-4a69-4dba-9dfb-fef4cc9332ae" TYPE="swap" 

biynayahu@biynayahu-laptop:~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system>                          <mount point>   <type>  <options>                        <dump>  <pass>
proc                                      /proc           proc    defaults                         0       0
# /dev/sda2
UUID=78cb62eb-3101-464a-b3e2-46773c2194af /               jfs     relatime,errors=remount-ro       0       1
# /dev/sda1
UUID=5b9f8393-de40-4fee-9c50-d6b140eb4395 /boot           ext2    relatime                         0       2
# /dev/sda0
UUID=7d4cc23a-79c7-4156-980a-3e948c0d6a83 /home           jfs     relatime                         0       2
/dev/scd0                                 /media/cdrom0   udf,iso9660 user,unhide,noauto,exec,utf8 0       0
usbfs                                     /proc/bus/usb   usbfs   devgid=14,devmode=0660           0       0

biynayahu@biynayahu-laptop:~$ df -m

Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda2                14613      5607      9006  39% /
tmpfs                      941         0       941   0% /lib/init/rw
varrun                     941         1       941   1% /var/run
varlock                    941         0       941   0% /var/lock
udev                       941         3       939   1% /dev
tmpfs                      941         1       941   1% /dev/shm
lrm                        941         3       939   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1                  118        44        69  39% /boot
/dev/sda3                95571     23280     72291  25% /home

---

### Post by Slim Odds on 2009-02-25
> **BiynaYahu said:**
> I'm currently in the process of re-partitioning without backing up my data.

That's **always** a good idea.   (not really)

---

### Post by BiynaYahu on 2009-02-25
I worked, though.  So, I'm pretty stoked on my new swap, and my extra space in my /home directory.

---

### Post by BiynaYahu on 2009-02-25
*bump*

---

### Post by taurus on 2009-02-25
Edit /etc/fstab and add this line to the end of it for your swap partition.

```

UUID=f2f28c8b-4a69-4dba-9dfb-fef4cc9332ae   none   swap   sw   0   0
```
Save it and run

```
sudo mount -a 
free -m
```

---

### Post by BiynaYahu on 2009-02-25
Thank you yet again taurus!

---

