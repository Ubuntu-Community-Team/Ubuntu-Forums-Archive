---
title: "Partitions on install"
date: 2009-01-20
forum: General Help
---

### Post by floatingpoint on 2009-01-20
Hello,

I was just reinstalling Ubuntu. When it came to partitioning, I chose to use the whole disk, to get rid of the previous installation (long story, [here]("http://ubuntuforums.org/showthread.php?t=1045436") if you're interested). I noticed that it made another small partition, Partition #5 or /dev/sda5. I had a wee look in /dev, and noticed sda, sda1, and sda5.

Are these all seperate partitions? What are they for?

---

### Post by dcstar on 2009-01-20
> **floatingpoint said:**
> Hello,

I was just reinstalling Ubuntu. When it came to partitioning, I chose to use the whole disk, to get rid of the previous installation (long story, [here]("http://ubuntuforums.org/showthread.php?t=1045436") if you're interested). I noticed that it made another small partition, Partition #5 or /dev/sda5. I had a wee look in /dev, and noticed sda, sda1, and sda5.

Are these all seperate partitions? What are they for?

You tell us, it is your machine:

```
sudo fdisk -l
mount
```

---

### Post by floatingpoint on 2009-01-20
```
kevin@kevin-desktop:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10731073

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9638    77417203+  83  Linux
/dev/sda2            9639       10011     2996122+   5  Extended
/dev/sda5            9639       10011     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc989c989

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS


kevin@kevin-desktop:~$ mount
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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)
kevin@kevin-desktop:~$ 

```

So, Linux is my Ubuntu installation. Well, it's my Linux installation. Linux Swap, is that like a pageing file? 

I dunno what Extended would be.

---

### Post by Dieseler on 2009-01-20
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9638    77417203+  83  Linux
/dev/sda2            9639       10011     2996122+   5  Extended
/dev/sda5            9639       10011     2996091   82  Linux swap / Solaris

sda is the disk itself.
/dev/sda1 is a primary partition and it contains your  Ubuntu install.
/dev/sda2 is an extended partition and it contains one logical partition,
/dev/sda5 which is your swap file.

A drive can contain only four primary partitions or three primary and one extended.
Extended partitions can contain several logical partitions, I'm not sure how many but quite a few.

---

### Post by jerome1232 on 2009-01-20
yes /dev/sdxx are devices paths for you partitions

ie /dev/sda is the first Disk (the entire disk)

/dev/sda1 would be the first partition on the first disk
/dev/sda2 would be the second partition on the first disk (in your case an extended partition that contains logical partitions)
/dev/sda5 would be the first logical partition on the first disk and so forth (there can only be 4 primary partitions on a disk)

/dev/sdb would be the second disk (the entire disk)

/dev/sdb1 would be the first partition on the second disk, it goes on.

If you write data to /dev/sdb1 it would write raw data to the disk, don't do this though it'll destroy your filesystem :)

---

### Post by floatingpoint on 2009-01-20
Hahah. Jerome, if I made sdb1 ext3 instead of NTFS, would writing data to it still destroy the filesystem?

---

### Post by jerome1232 on 2009-01-20
> **floatingpoint said:**
> Hahah. Jerome, if I made sdb1 ext3 instead of NTFS, would writing data to it still destroy the filesystem?

Yeah, because it's just writing raw data to a disk.

The first 512 bytes of your hard drive contain the boot record and partition table, if you overwrite that, your drive wouldn't know where the partition's on it are even located at.

---

### Post by floatingpoint on 2009-01-21
Oh right, Well... I'll try to avoid doing that then! :P 

Thanks for the information guys. :D

---

