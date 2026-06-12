---
title: "help with unmounting and mounting external?"
date: 2009-04-05
forum: General Help
---

### Post by shateredsoul on 2009-04-05
Hi, 

I was wondering if someone could help me figure out how to mount and unmount external harddrives in my computer. 

I have no clue where to start, and the threads I usually found where specific to a person's situation.

I would appreciate any help.

---

### Post by kanikilu on 2009-04-05
Hi, what desktop environment are you using? The default Gnome should try to automatically mount your external drives in /media/<label>. Does it give you an error or something?

If they don't mount automatically, try plugging one in and open a terminal (Applications > Accessories > Terminal), and then separately copy and paste into a reply the output of the following commands:```
mount
sudo fdisk -l
``` Please put the output in code tags so we can read it: &#91;code&#93;output here&#91;/code&#93;

---

### Post by shateredsoul on 2009-04-05
So I get this when i put that in, to answer some of your questions.  I'm using ubuntu with gnome (that's what it comes with right?), and it used to mount and unmoutn automatically.  One day while I was using a program that was accessing files on the external I accidentally disconnected it and have had problems since then. It says "you are not priveleged to mount" or "unmount".  The output might show that pheonix is recognized, because I force mounted it.  I used to use the ntfs config tool, because after using it it used to mount (not today), but I still had the privilege issue when unmounting. If I should unmount the drive and do this again without it force mounted please let me know.

```
omar@omar-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/omar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=omar)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /media/Phoenix type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
omar@omar-laptop:~$ sudo fdisk -l
[sudo] password for omar: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
omar@omar-laptop:~$ 

```

---

