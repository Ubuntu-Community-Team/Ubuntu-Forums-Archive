---
title: "One of three volumes is shown in nautilus as volume as well as folder"
date: 2008-07-13
forum: Desktop Environments
---

### Post by mazz0 on 2008-07-13
Hi Guys,

I have four partitions in total.

**a** with Ubuntu on it
**b** with Windows on it
**c** with all my files on it except for videos
**d** with my videos on it

Those are just arbitrary letters I'm referring to them by here - nothing to do with Windows drive letters.

I have them mounted as follows:

**a** as / (obviously!)
**b** as /Windows
**c** as /home/mazz0
**d** as /home/mazz0/Videos

Took me a while to get that arrangement working, with one volume mounted within another, but in the end I found that all I had to do was make sure c was mounted before d!

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system>                               <mount point>        <type>        <options>                   <dump>  <pass>
proc                                          /proc                proc          defaults                    0       0
# /dev/sdb3
UUID=1abd3705-f562-437f-8565-f15c00250c2f     /                    ext3          relatime,errors=remount-ro  0       1
# /dev/sdb2
UUID=6c6a8e0a-e47f-4e52-9b77-7b3c456c7332     none                 swap          sw                          0       0
# /dev/sdc5
UUID=c8b892ea-a4d1-4c24-9ff5-3f3e27b9167f     none                 swap          sw                          0       0
/dev/scd0                                     /media/cdrom0        udf,iso9660   user,noauto,exec,utf8       0       0
# 300GB drive as home folder for mazz0
/dev/sdc1                                     /home/mazz0          ext3          relatime,errors=remount-ro  0       0
# 500GB drive as Videos folder for mazz0
/dev/sda1                                     /home/mazz0/Videos   ext3          relatime,errors=remount-ro  0       0
# 120GB drive as Windows
/dev/sdb1                                     /Windows             ntfs          relatime,errors=remount-ro  0       0
```

Everything works fine, my only issue is this: partition **d** (/home/mazz0/Videos) shows as a volume in Nautilus!  It shows in the correct place as a folder as well, which is where it takes you when you open the volume in Nautilus, but I don't want it to be shown as a volume too!  Partitions **a**, **b** and **c** are not shown as volumes.

Any suggestions?

---

### Post by sayakb on 2008-07-13
**a **is shown as Filesystem
**b: **You should mount the /dev/sdb1 as /media/Windows to show it up as a volume
**c: **The home folder (/home/username) is never shown up as a volume.
**d: **Not sure about this.. Its showing up 400.1GB media in the Computer, while it is a 500GB volume as your fstab indicates?

---

### Post by tech0007 on 2008-07-13
paste the output of 'sudo fdisk -l /dev/sdX'

substitute X with a, b & c for all 3 drives

---

### Post by mazz0 on 2008-07-13
@ LinuxIsInnovation

Yeah - I thought only things in /media or /mnt would show up as volumes, which is why I don't understand why my 400gb volume shows up as one when it's not mounted in either of those folders.  Thing is, I don't want *any* of them to show up as volumes, I only want removable media as volumes.

Oh, and it says 500gb drive in the comment in my fstab cos it's a 500gb drive, but I only get 400.1gb of that when formatted (that's as Ext3 - I think it was 375gb as NTFS -is that cos ext3 is better or is it more complicated than that?)

@ Tech0007

```
mazz0@mazz0-linux:~$ sudo fdisk -l /dev/sda
[sudo] password for mazz0: 

Disk /dev/sda: 400.0 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xab7ffcbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       51682   390709248   83  Linux
mazz0@mazz0-linux:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76af7ed1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7012    56320000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            7013        7620     4883760   82  Linux swap / Solaris
/dev/sdb3            7621       15017    59416402+  83  Linux
mazz0@mazz0-linux:~$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000458b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36483   293049666   83  Linux

```

---

