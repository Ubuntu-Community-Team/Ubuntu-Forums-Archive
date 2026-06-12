---
title: "data on a fat drive can´ be exported to anything...."
date: 2006-01-29
forum: Desktop Environments
---

### Post by cmongini on 2006-01-29
something strange happens: i have some data on a fat drive ( they are the residuum from when the win xp  was on the machine), by logging in as root i copied them to my ext3 drive, there i changed the permission to 777 with chmod. I can access them but there is no way i can export them ( i can´t burn them to dvd, although the gnomemaker works with other things, i can´t export them to an external drive, where also i have no problems to export other files, i can´t export them via ftp to an other computer. any suggestions?

---

### Post by aysiu on 2006-01-29
Don't bring them over as root and chmod them.
Just mount them with the proper permissions.
See the fourth link of my signature.

---

### Post by cmongini on 2006-01-29
thanks for the hint, i did it, but although i gave umask 000 permissions as shown in the page, my files were still only read and execute files, not writable....

---

### Post by aysiu on 2006-01-29
Well, let's take a look at what's going on. Can you post the output of these three commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by cmongini on 2006-01-29
ok thanks the drive in question is hda5:

Disk /dev/hda: 40.0 GB, 40027029504 bytes
16 heads, 63 sectors/track, 77557 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23250    11717968+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           23253       77552    27366727+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/hda3           76070       77552      746991   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/hda5           23253       76070    26619642    b  W95 FAT32

Disk /dev/hdb: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2               1        2490    20000893+   5  Extended
/dev/hdb5            2398        2490      746991   82  Linux swap / Solaris
/dev/hdb6               1        1094     8787460+  83  Linux
/dev/hdb7            1095        2397    10466316   83  Linux
------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       /home           ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda5 /media/hda5 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0

/dev/hdb6             8.3G  3.0G  4.9G  39% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-10-386/volatile
/dev/hdb7             9.9G  6.4G  3.0G  69% /home
/dev/hda1              12G  543M   11G   5% /media/hda1
/dev/hda5              26G  9.5G   16G  38% /media/hda5


the fact is that as i had to reinstall ubuntu twice, i copied all the data from an ntfs drive to the fat drive, then reformatted the ntfs drive in the new installation ( so the data are not there anymore...) this might have caused the problem...

---

### Post by cmongini on 2006-01-29
the problem seems to be solved as now i´ m half thru putting my data on the laptop  by the "connect to server" option....all the other possibes still don´t work but one is enough! 
an other problem has arisen though. i have two phisical drives in the pc,  linux is on a partition of the slave drive, Grub is on the master. when the  fat data are fully copied (also on the master), i would like to reformat the master drive ( hda).
if i open gparted, it tells me that by setting a new label ( what i understood is necessary to reformat one or more partitions), all my data on the physical drive (hda) will be deleted. that would mean that grub too would be deleted and i wouldn´t be able to start anymore the system...
is there a way out? 
thanks

---

### Post by aysiu on 2006-01-29
[QUOTE=cmongini] 
an other problem has arisen though. i have two phisical drives in the pc,  linux is on a partition of the slave drive, Grub is on the master. when the  fat data are fully copied (also on the master), i would like to reformat the master drive ( hda).
if i open gparted, it tells me that by setting a new label ( what i understood is necessary to reformat one or more partitions), all my data on the physical drive (hda) will be deleted. that would mean that grub too would be deleted and i wouldn´t be able to start anymore the system...
is there a way out? 
thanks[/QUOTE] I'm not sure I understand your situation exactly, but maybe [this](http://ubuntuforums.org/showthread.php?t=24113) might help?

---

### Post by cmongini on 2006-01-30
sounds good, in the case gparted deletes all the drive, it seems to be an easy solution, thanks!

---

### Post by cmongini on 2006-01-30
ok i repartitioned my hda drive (only one partition hda1) but i can´t mount it....
i followed the descriprion you gave me for mounting windows partitions, and by  doing sudo nano /etc/fstab i noticed that he was still trying to mount the old partitions. so i reedited the stab file. the drive (hda1) now mounts correctly, but it has only root permissions! i mocked aroung a bit but couldnt find the right values, to allow ALL permissions

here are the values:

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/hda1               1        4866    39086113+  83  Linux[/COLOR]

Disk /dev/hdb: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2               1        2490    20000893+   5  Extended
/dev/hdb5            2398        2490      746991   82  Linux swap / Solaris
/dev/hdb6               1        1094     8787460+  83  Linux
/dev/hdb7            1095        2397    10466316   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       /home           ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
[COLOR="Red"]/dev/hda1       /media/disk3    ext3    defaults,        0      2[/COLOR]
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb6             8.3G  2.8G  5.2G  35% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-10-386/volatile
/dev/hdb7             9.9G  6.4G  3.0G  69% /home
[COLOR="Red"]/dev/hda1              37G  129M   35G   1% /media/disk3[/COLOR]

thanks

---

### Post by cmongini on 2006-01-30
i found just now your reply to the thread 
[http://www.ubuntuforums.org/showthread.php?t=116804&highlight=mount+ext3+permissions](http://www.ubuntuforums.org/showthread.php?t=116804&highlight=mount+ext3+permissions)
if i can change the permissions later then the problem is solved, thanks anyway!

---

