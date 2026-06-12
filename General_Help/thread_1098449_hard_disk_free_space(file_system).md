---
title: "hard disk free space(file system)"
date: 2009-03-17
forum: General Help
---

### Post by kask1984 on 2009-03-17
hi every body i installed ubuntu 8.10 after installing windows xp.i allocated 90GB to ubuntu .i have stored my music,movie ec files in ubuntu partition. it is around 62GB(nearly)  but the free space showing is only 2GB(nearly).where is the remaining space.
please help me.
thanks

---

### Post by Herman on 2009-03-17
The most common reason for the partition to seem full when viewed with some programs when you know it's really not full is the file system not having been made as large as the partition it is in, for some reason.
Some programs look at the partition and tell you it's not full and other programs are looking at the file system and telling you that the file system is full.
Both may be correct. The partition is like a container which the file system is housed in.

[LIST=1]
[*]Boot your Live CD, open Gnome Partition Editor and right-click on the partition you want checked. Look in 'System-->'Administration'-->'Partition Editor'.
[*]Right-click on your Ubuntu partition and select 'check' from the right-click menu. If 'check' is greyed out you might need to select 'unmount first, then click 'check'.
[*]Click the 'Apply'  check mark button up on the toolbar.
[*]Click the 'Apply' button in the confirmation pop-up window
[*]Watch the reciprocating bar for a few minutes, a very large file system may take a while
[*]Click on the 'Details' triangle to expand the window
[*]Click on the triangle in front of 'Check and repair filesystem (ext3_ on ....)' for details
[*]If it's the Ext3 file system, GParted will have calibrated your file system first, run e2fsck -f -y -v on it for you, and finally run resize2fs for you to make sure your file system is the right size to fill your partition.
[/LIST]

---

### Post by hyper_ch on 2009-03-17
post the output of

```

df -h

```

and

```

sudo fdisk -l

```

---

### Post by kask1984 on 2009-03-17
output of df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              89G   82G  2.3G  98% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M   84K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  497M   1% /dev
tmpfs                 500M  272K  500M   1% /dev/shm
lrm                   500M  2.0M  498M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/scd0             158M  158M     0 100% /media/cdrom0
/dev/sdb1             2.0G  2.6M  2.0G   1% /media/disk
/dev/sdc1             2.0G  556M  1.4G  29% /media/SHIVA


output of sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe88be88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        7648    30716280    f  W95 Ext'd (LBA)
/dev/sda3            7649        7710      498015   82  Linux swap / Solaris
/dev/sda4            7711       19457    94357777+  83  Linux
/dev/sda5            3825        7648    30716248+   7  HPFS/NTFS

Disk /dev/sdb: 4089 MB, 4089446400 bytes
251 heads, 49 sectors/track, 649 cylinders
Units = cylinders of 12299 * 512 = 6297088 bytes
Disk identifier: 0x4af14af0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         326     1999928    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 15)
Partition 1 has different physical/logical endings:
     phys=(248, 250, 49) logical=(325, 55, 49)

Disk /dev/sdc: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xdd4328cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7840     2007024    b  W95 FAT32

---

### Post by ugm6hr on 2009-03-17
> **kask1984 said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              89G   82G  2.3G  98% /

You have 82GB of data on there.

Have you run a backup?

Or copied and deleted files (but not emptied trash) etc?

---

### Post by kask1984 on 2009-03-17
no i did not run backup

---

### Post by ruel- on 2009-03-17
maybe you have doubled some files, trashed some big ones.. or moved in different locations in the filesystem.. recheck your root folder and trash.,.

---

### Post by ifyc576 on 2009-03-18
I also am quite new to Ubuntu.  When I read this post, I was reminded to check for hidden files and/or folders.  In Nautilus hit Ctrl H

I found a hidden folder that should have been trashed.

I was able to delete the folder and regain the hard disk space.

Hope this helps...

---

### Post by =Planta= on 2009-03-19
Hello there,

I believe Baobab (included by default in your Ubuntu 8.10) could be a great graphical tool for you to figure out which are the "villain directories" that take up so much space unexpectedly. It even deals with Linux hidden files and directories. You can access it by:
[LIST]
[*]**Main Menu -> Accessories -> Disk Usage Analyzer**
or, from a terminal,
[*]**$ baobab &**
[/LIST]
Then, to use it :
[LIST=1]
[*] Click on the "Scan Filesystem" button
[*] (Wait...)
[*] Use the left panel to select directories and view per-directory disk usage data. You can use the graphical circular tree on the right to do the same, by hovering over a directory to have data popping up (after a <1sec delay), and by double-clicking an arc to make its directory the new root of the circular tree.
[*] Track the big ones. ;)
[/LIST]

My machine is a dual/multi-boot like yours, but I keep Ubuntu in a reiserfs 8GB partition, and all personal files in a huge separate NTFS partition. Works fine, Ubuntu fits and the data is readable by both operating systems with no additional tweaks - I suggest you to do the same in a future installation.

== Apart from that... ==
By the way, what is going on with whichever storage device is under your /dev/sdb?
> **kask1984 said:**
> 
output of sudo fdisk -l
**Disk /dev/sdb: [COLOR="Red"]4089 MB[/COLOR], 4089446400 bytes**
251 heads, 49 sectors/track, 649 cylinders
Units = cylinders of 12299 * 512 = 6297088 bytes
Disk identifier: 0x4af14af0
   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *           1         326     [COLOR="Red"]1999928[/COLOR]    b  W95 FAT32**
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 15)
Partition 1 has different physical/logical endings:
     phys=(248, 250, 49) logical=(325, 55, 49)

It seems to be a 4GB device but with only one partition (/dev/sdb1) that uses only half of its capacity... Not to mention this creepy warning about physical/logical beginnings.. Are you aware of this?
As you have only 2.6M of personal data in there ...
> **kask1984 said:**
> 
output of df -h
/dev/sdb1             2.0G  2.6M  2.0G   1% /media/disk

... it would be pretty easy to backup this and then partition and format the device properly. **If you are going to do it, make sure this device is really under /dev/[COLOR="Red"]sdb[/COLOR] when following the instructions below:**

PARTITIONING, as root, from a terminal:
**# fdisk /dev/sdb**
**fdisk> d** (deletes the only partition, sdb1)
**fdisk> n** (start creation of new partition)
**fdisk>>> p** (for primary)
**fdisk>>> Enter** (for default first_cylinder=1)
**fdisk>>> Enter** (for default last_cylinder=last, thus using the entire device)
**fdisk> t** (to set the type of the partition)
**fdisk>>> b** (for a FAT32 partition) OR l (for more options if this device is not a USB stick, then the 1-2 letter code for the desired option)
**fdisk> w** (apply these changes and quit) OR q (quit without modifying your device, as if you never entered fdisk)

FORMATING, as root, from a terminal:
**# mkfs.vfat /dev/sdb1**

Unplug and replug your device to see the changes.

CHECKING, as root, from a terminal:
[B]# fdisk -l /dev/sdb
# df -haT /dev/sdb[/B]

Best of luck,
Planta.

---

### Post by kask1984 on 2009-03-19
hai planta, 
thanks for u r suggestions.
u r solution for my free space problem is solved. i tracked the large files and i deleted them( which were not useful to me).
4GB device is actually a pen(flash) drive.it is my friends pendrive.
 u r correct that, even though it is 4GB capacity,system is recognizing only 2GB(half)
can u elaborate u r solution i am not  able to follow.( i tried whatever i understood,  (i executed commands as u posted) but it is not working )
thanks....

---

### Post by kask1984 on 2009-03-19
hai planta, 
thanks for u r suggestions.
u r solution for my free space problem is solved. i tracked the large files and i deleted them( which were not useful to me).
4GB device is actually a pen(flash) drive.it is my friends pendrive.
 u r correct that, even though it is 4GB capacity,system is recognizing only 2GB(half)
can u elaborate u r solution i am not  able to follow.( i tried whatever i understood,  (i executed commands as u posted) but it is not working )
thanks....

---

### Post by kask1984 on 2009-03-30
hi planta i am waiting for u r reply

---

