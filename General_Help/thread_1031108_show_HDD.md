---
title: "show HDD"
date: 2009-01-05
forum: General Help
---

### Post by slickuser on 2009-01-05
I have two HDs on my computer, Primary, Xubuntu OS, I want to transfer all my data from the second drive to my external HD. 
It's not showing up from Xubuntu live cd either.

Any idea? Also, how can I verify that my HD is not defect because I'm suspecting of the new HD is failing. Thanks.

---

### Post by iaculallad on 2009-01-05
On your terminal, you could try:

list all your hard drives with:

```
sudo fdisk -l
```

then, using e2fsck (badblock):

```
e2fsck -c /dev/xxx
```

xxx = the drive you want to check for errors.

---

### Post by slickuser on 2009-01-07
How can I transfer data from sdb to sdc?

Thanks.

> 
Disk /dev/sda: 640.1 GB, 640135028736 bytes
103 heads, 29 sectors/track, 418568 cylinders
Units = cylinders of 2987 * 512 = 1529344 bytes
Disk identifier: 0xb5d7d25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      418568   625129472    7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5d7d244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77826   625129472    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    c  W95 FAT32 (LBA)



>> mount
> 
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)



> ubuntu@ubuntu:~$ e2fsck -c /dev/sda
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Permission denied while trying to open /dev/sda
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ sudo e2fsck -c /dev/sda
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


---

### Post by slickuser on 2009-01-09
Is that mean that I have a bad HD?

---

### Post by logos34 on 2009-01-09
e2fsk is for linux fs...can't run it on NTFS, but I don't think that's your prob

sdb1 isn't mounting

try

sudo mkdir /media/sdb1

sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

---

