---
title: "Cannot use /etc/fstab to mount fuse filesystem on boot"
date: 2009-02-17
forum: General Help
---

### Post by aschoessler on 2009-02-17
Hello,

I'm trying to get an NTFS drive mounted under a fresh install of Ubuntu 8.1. The NTFS drive is just data; no Windows installation is on it. It just seems like a good way to share large amounts of data between Ubuntu and my Windows 7 installation.

Anyway, it seems that Ubuntu has fuse preinstalled, and I can mount the drive via the File Browser.

Here is the output of sudo mount after I manually mount the filesystem via the File Browser:

```
$ sudo mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda3 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aschoessler/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aschoessler)
/dev/sdc1 on /media/disk-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

/dev/sdc1 is the NTFS filesystem I would like to be permanently mounted. When it is mounted manually from the File Browser, I can access the filesystem. I even copied a whole bunch of data to it earlier.

Here is /etc/fstab:

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5f5c65ab-2069-42b3-a707-cd5a656d2ca7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=b8b331bb-0754-4ac0-a285-15d30ebb2ec5 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=15d33fb2-dbb5-428c-ae6c-5f8916041e1b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

By following the guidelines at [http://ubuntuforums.org/showthread.php?t=550522](http://ubuntuforums.org/showthread.php?t=550522), I added the following to /etc/fstab:

```
/dev/sdc1 /media/disk-2 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
```

(I tried it with the exact options on that user's fuse entries as well).

I then unmounted the filesystem via the File Browser, and executed:

```
$sudo mount -a
```

I get the following error:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I'm going with "other error" because the drive mounts and works just fine when I mount it from the file browser. 

```
$ tail /var/log/syslog
Feb 16 21:36:59 SATURN -- MARK --
Feb 16 21:56:59 SATURN -- MARK --
Feb 16 22:15:17 SATURN ntfs-3g[10026]: Version 1.2506 external FUSE 27 
Feb 16 22:15:17 SATURN ntfs-3g[10026]: Mounted /dev/sdc1 (Read-Write, label "", NTFS 3.1) 
Feb 16 22:15:17 SATURN ntfs-3g[10026]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
Feb 16 22:15:17 SATURN ntfs-3g[10026]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096 
Feb 16 22:15:17 SATURN hald: mounted /dev/sdc1 on behalf of uid 1000
Feb 16 22:17:01 SATURN /USR/SBIN/CRON[10044]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 16 22:18:49 SATURN ntfs-3g[10026]: Unmounting /dev/sdc1 () 
Feb 16 22:18:49 SATURN hald: unmounted /dev/sdc1 from '/media/disk' on behalf of uid 1000
```

I'm not sure why it says '/media/disk' instead of '/media/disk-2'
Is mount -a not the correct way to test this?

Any ideas out there?

---

### Post by cariboo on 2009-02-17
Use ntfs-3g to mount your drive instead of fuse. Fuse is only used when automounting a drive in Nautilus.

Jim

---

### Post by Tim Sharitt on 2009-02-17
Try using ntfs-3g instead of fuseblk

fstab line:
```
/dev/sdc1 /media/disk-2 ntfs-3g defaults 0 0
```

The tutorial you are using may be a bit dated.

---

### Post by aschoessler on 2009-02-18
> **Tim Sharitt said:**
> Try using ntfs-3g instead of fuseblk

fstab line:
```
/dev/sdc1 /media/disk-2 ntfs-3g defaults 0 0
```

The tutorial you are using may be a bit dated.

Thanks a lot--that worked great!

---

