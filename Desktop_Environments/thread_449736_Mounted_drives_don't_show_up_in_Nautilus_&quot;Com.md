---
title: "Mounted drives don't show up in Nautilus &quot;Computer&quot; view"
date: 2007-05-20
forum: Desktop Environments
---

### Post by shifuimam on 2007-05-20
I have two physical hard drives in my system - one on IDE 0 and one on SATA 0. The IDE drive is my OS drive, housing my Ubuntu root and swap partitions, a Windows XP partition (NTFS), and an NTFS extra data partition from the left over space. The second drive has two data partitions - one FAT32 and one NTFS. I also have two optical drives on IDE 1 - a DVD+/-RW and a DVD-ROM, as well as a 3.5" floppy.

If I go to Places > Computer on the main menu bar in Gnome, Nautilus will only display my two optical drives, my floppy drive, and "Filesystem". I have to actually navigate to /media/ to see my partitions, which do mount and are fully accessible. I'd really like to be able to see my logical drives in the Computer view, though, since I access them so frequently. My local Ubuntu expert cannot figure out how to change the config for Nautilus, so I figured I'd ask here. Screenshot below to clarify my problem:

[img]http://shifuimam.googlepages.com/Screenshot-Computer-FileBrowser.png[/img]

Any help is really appreciated.

---

### Post by bapoumba on 2007-05-20
From the terminal, run **gconf-editor**.
Apps > Nautilus > Desktop > is volume visible ticked ?
Anything mounted in /media will show up on your desktop.

---

### Post by shifuimam on 2007-05-20
volumes_visible is indeed ticked.

Incidentally, nothing is showing up on my desktop anymore. Strange.

---

### Post by bapoumba on 2007-05-20
What do return:
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by shifuimam on 2007-05-20
My fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=dcfe2d52-9a4a-47cc-8973-dfe88fb8f788 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=029C0F839C0F7089 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=7AF47ECBF47E88E1 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=58143E9A143E7AD8 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=4605-60A5  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=c5a2a6e7-72fc-4e97-9b25-51fa917caa7c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5221    41937651    7  HPFS/NTFS
/dev/sda2           10444       19457    72402272+   7  HPFS/NTFS
/dev/sda3           10320       10443      996030   82  Linux swap / Solaris
/dev/sda4            5222       10319    40949685   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12161    97683201    7  HPFS/NTFS
/dev/sdb2           12162       24321    97675200    f  W95 Ext'd (LBA)
/dev/sdb5           12162       24321    97675168+   b  W95 FAT32

```

---

### Post by bapoumba on 2007-05-20
Hum. I'm not an expert with this, and do not have a windows partition anymore. But it used to mount  on the desktop when mounted on /media.

Are cdroms showing up on your desktop when you insert one in the drive ? Or floppies ?

---

### Post by shifuimam on 2007-05-20
They were, but not anymore. Sometime in the last few hours, all the icons on my desktop - including stuff in my Desktop folder - doesn't display on the desktop anymore. :(

---

### Post by bapoumba on 2007-05-21
Did you run an upgrade ? If so, do you remember which packages were upgraded ? Did you install something ?

Have you tried to log out and log back in your session ?

Is it the same with another user ? (you can make one with **sudo adduser test**, assuming "test" is the new user). If a new user has no problem, then we'll have to look at your regular user config files.

---

### Post by crane on 2007-05-21
Try running ```
mount
``` in the terminal and see if everything is still mounted.
As mentioned earlier, have you logged out and back in, or restarted?

Keep us posted.

---

### Post by shifuimam on 2007-05-23
Sorry about the delay. I've been busy lately with real life. :\

Results of running "mount":

```

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-12-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb5 on /media/sdb5 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

As you can see, sda1 and sda2 are my primary (IDE) drive, both NTFS partitions - XP install and a data part. sdb1 and sdb5 are my secondary (SATA) drive, one each FAT32 and NTFS data parts.

Incidentally, I also have another thread that has gotten ignored, [here](http://ubuntuforums.org/showthread.php?t=449729). Any help on that one is also appreciated - it's driving me far nuttier than this Nautilus issue, since the janky resolution on my primary display makes it impossible to use said display.

Thanks!

---

