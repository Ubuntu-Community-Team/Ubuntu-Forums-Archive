---
title: "Unable to mount"
date: 2009-04-14
forum: General Help
---

### Post by dE_logics on 2009-04-14
I set the mount point of a partition as /home in the properties dialogue of the partition and there's no way its getting mounted now.

how do I get things to normal?


Also tell me how do I auto mount a partition.

---

### Post by askreet on 2009-04-14
Things you set in the GUI are all post-bootup.  Please open a terminal and give us the output of:
```
df -h
```
and
```
mount
```
and
```
cat /etc/fstab
```

Thanks!
- askreet

---

### Post by dE_logics on 2009-04-14
df -h says - 
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.3G  2.0G  7.4G  22% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M   72K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.7M  497M   1% /dev
tmpfs                 500M  104K  500M   1% /dev/shm
lrm                   500M  2.0M  498M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda1              61M   18M   41M  30% /boot

```

---

### Post by dE_logics on 2009-04-14
This is what mount says - 
```
/dev/sda7 on / type jfs (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/de/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=de)

```

This is for the fstab one - 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=5b5c21a3-4355-442b-9a39-69eb8a5c2dc4 /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=a1e3be50-a22c-48ce-9b50-979056636ad1 /boot           ext3    relatime        0       2
# /dev/sda10
UUID=4ce612af-769d-47ea-a08e-796c08c8488d none            swap    sw              0       0
# /dev/sda8
UUID=ad3f69ce-d708-4fa9-98a3-34f132caf0cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by askreet on 2009-04-14
That all looks normal, is /home missing?  What does:
```
ls -l /
```

have to say?

---

### Post by dE_logics on 2009-04-15
```
total 105
drwxr-xr-x   2 root root  4096 2009-04-14 12:13 bin
drwxr-xr-x   4 root root  1024 2009-04-14 12:00 boot
lrwxrwxrwx   1 root root    11 2009-04-14 11:40 cdrom -> media/cdrom
drwxr-xr-x  15 root root 14100 2009-04-15 00:49 dev
drwxr-xr-x 123 root root  8192 2009-04-15 00:49 etc
drwxr-xr-x   3 root root     8 2009-04-14 11:57 home
lrwxrwxrwx   1 root root    32 2009-04-14 12:00 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2009-04-14 12:13 lib
drwxr-xr-x   6 root root  4096 2009-04-15 00:49 media
drwxr-xr-x   2 root root     1 2008-10-20 08:27 mnt
drwxr-xr-x   2 root root     1 2008-10-29 20:41 opt
dr-xr-xr-x 128 root root     0 2009-04-15 00:45 proc
drwxr-xr-x  11 root root  4096 2009-04-14 15:12 root
drwxr-xr-x   2 root root  4096 2009-04-14 12:13 sbin
drwxr-xr-x   2 root root     1 2008-10-29 20:41 srv
drwxr-xr-x  12 root root     0 2009-04-15 00:45 sys
drwxrwxrwt  12 root root  4096 2009-04-15 00:47 tmp
drwxr-xr-x  11 root root    72 2008-10-29 20:46 usr
drwxr-xr-x  15 root root  4096 2008-10-29 21:00 var
lrwxrwxrwx   1 root root    29 2009-04-14 12:00 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

```

---

### Post by dE_logics on 2009-04-15
CAN SOMEONE HELP ME PLEASE!! :mad:

---

