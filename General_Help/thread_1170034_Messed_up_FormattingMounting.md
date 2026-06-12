---
title: "Messed up Formatting/Mounting"
date: 2009-05-25
forum: General Help
---

### Post by jtdeloach10 on 2009-05-25
This morning I installed a second hard drive. It is an 80 GB. FDISK -l recognizes it like so:


Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9726    78124063+  83  Linux

When I go to mount it as my /www, it mounts successfully yea! Or so you think!

Using, *sudo mount /dev/sdb1 /www* I mount it with no errors! Cool! 

But df -H outputs:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               20G   1.1G    18G   6% /
tmpfs                   62M      0    62M   0% /lib/init/rw
varrun                  62M    87k    62M   1% /var/run
varlock                 62M      0    62M   0% /var/lock
udev                    62M   160k    62M   1% /dev
tmpfs                   62M      0    62M   0% /dev/shm
lrm                     62M   2.5M    60M   4% /lib/modules/2.6.28-11-server/volatile
/dev/sdb1               40M   4.7M    34M  13% /www

And it is only 40m instead of 80g! I'm kind of getting ripped here ;)

---

### Post by drs305 on 2009-05-25
Have you tried looking at it with gparted?
```

gksudo gparted /dev/sdb

```

---

### Post by jtdeloach10 on 2009-05-25
I am using server, therefor no gui.
Any other ideas?

---

### Post by jtdeloach10 on 2009-05-26
Umm, this, to me, is a very important thread and I need it solved. B.u.m.p.

---

### Post by swimmin on 2009-05-26
I am having the same problems, answers anyone?? I have no idea how to conquer this and it's really frusterating!

---

### Post by jtdeloach10 on 2009-05-26
Hey! good to know someone else is having a similar problem. if only someone would answers they could kill two problems with one stone!

---

### Post by jtdeloach10 on 2009-05-26
Hey just so more info incase it will help you guys solve our problem:

fsck says:
********@*******:~$ sudo fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb1: clean, 1211/10040 files, 19286/40128 blocks

Mount says:
*********@******:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-server/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /www type ext3 (rw)

---

### Post by Boondoklife on 2009-05-26
Well if I were you I would just use fdisk to repartition the disk and then mkfs to create the filesystem and try mounting it again.

It could be that the drive is not formatted or partitioned correctly from the factory, I personally have seen this a few times.

also can you post the output of```
ls /dev/sd*
```

---

### Post by jtdeloach10 on 2009-05-26
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdb1



I will work on repartitioning and formatting it again, I'll post with updates.

---

### Post by jtdeloach10 on 2009-05-26
Reformatting was the trick! Thanks for the help!

---

### Post by Boondoklife on 2009-05-26
> **jtdeloach10 said:**
> Reformatting was the trick! Thanks for the help!

no prob

---

