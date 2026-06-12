---
title: "Unable to find mountpoint blues"
date: 2009-04-20
forum: General Help
---

### Post by clovenage on 2009-04-20
Hello

Trouble with my 8.04 install.

GParted reports:

> Warning
Unable to find mountpoint
Unable to read the contents of the filesystem!
Because of this some operations may be unavailable

How can the machine even be running it it can find the operating system files?

Here is my list of mounts:

> michael@ultraman:~$ mount -l
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal) []


Here is what my fstab is like:


> michael@ultraman:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c0da75da-b434-4c39-9dd5-80f6d614a20b /dev/sda1               ext3    rw       1
# /dev/sda5
UUID=7ba9549e-6d8e-4b37-a53f-b0515199752b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


This problem is preventing me from creating a VMWare machine image of this OS, any help would be appreciated. 

Thanks

---

### Post by cariboo on 2009-04-21
I'm not sure you have a running system, but you don't have a mount point for /dev/sda1. It should look something like this:

```
# /dev/sda1
UUID=c0da75da-b434-4c39-9dd5-80f6d614a20b / ext3 relatime,errors=remount-ro 0       1
```

Jim

---

