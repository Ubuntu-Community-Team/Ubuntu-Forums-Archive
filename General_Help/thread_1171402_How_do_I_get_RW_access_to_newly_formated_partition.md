---
title: "How do I get R/W access to newly formated partition?"
date: 2009-05-27
forum: General Help
---

### Post by Ascenti0n on 2009-05-27
I deleted an NTFS partition from within WinXP and then booted up my Jaunty OS which resides on another HDD. I started 'Partition Editor' and created a new partition using the space from the partition deleted in Windows. The new partition was given a name and formatted to ext4.

Ubuntu 9.04 now recognises the new partition and it was mounted automatically, but I cannot create folders or files etc. I guess it is a permissions problem, but how do I give myself permission / access to the newly created partition?

---

### Post by hal8000 on 2009-05-27
Post the output of :
cat /etc/fstab


and also:


sudo fdisk -l


The partition has to be mounted before it can be read and wrote to, did you create a mount point and mount the partition?

---

### Post by Ascenti0n on 2009-05-27
I did nothing to fstab or mounts, Jaunty seems to have done this automatically. The partition in question is sdc2

Here is the output from first command:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e420aa03-4639-4acc-b486-af3402d6d88a /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=3b1ea379-308d-47ef-8cd2-de50c2dd7b1c /home           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=e276cfad-9866-4ccd-9e03-5863c88e81e2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0




here is the output from the second command:


Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x93a093a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     4815688+   b  W95 FAT32
/dev/sda2   *         638       10336    73324440    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6efd6ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3735    30001356   83  Linux
/dev/sdb2            3736       20023   130833360    5  Extended
/dev/sdb5            3736        4432     5598621   82  Linux swap / Solaris
/dev/sdb6            4433       20023   125234676   83  Linux

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ef7f91a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       11726    94182448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2           11727       20023    66645652+  83  Linux

---

### Post by Ascenti0n on 2009-05-27
can anyone continue to help? I feel naked after exposing my system info for all the world to see, and I have nothing to show for it ;)

---

### Post by Boondoklife on 2009-05-27
are you trying to write to it as a user or root?

if as a user try as root, if this works then joy you just need to change the permissions.

post the output of 
```
mount
```you can change the permissions to the drive by doing the following:
```
sudo chown USERNAME:GROUPNAME /media/DRIVE -R
sudo chmod 0755 /media/DRIVE -R
```Replace USERNAME with your username and GROUPNAME with your groupname, normally they are the same. Replace DRIVE with the mount point for that drive.

---

### Post by Ascenti0n on 2009-05-27
Thanks maletek. here is the output from the mount command:

> mount
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb6 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/briand/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=briand)
/dev/sdc1 on /media/DSK02 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc2 on /media/DSK03i type ext4 (rw,nosuid,nodev,uhelper=hal)

I will now try the other commands you mentioned in your post

---

### Post by Boondoklife on 2009-05-27
looks like /media/DSK03i is the mount point you will want to play with. can you post the output of ```
ls -l /media/DSK03i
```

---

### Post by Ascenti0n on 2009-05-27
@maletek. I followed the advice given above, rebooted my PC and now have read and write access to the new partition.

Thanks for your help :D

---

### Post by Boondoklife on 2009-05-27
> **Ascenti0n said:**
> @maletek. I followed the advice given above, rebooted my PC and now have read and write access to the new partition.

Thanks for your help :D

Glad ta help

---

