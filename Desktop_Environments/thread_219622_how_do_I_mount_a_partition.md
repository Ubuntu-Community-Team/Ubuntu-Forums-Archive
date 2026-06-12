---
title: "how do I mount a partition"
date: 2006-07-20
forum: Desktop Environments
---

### Post by ShirishAg75 on 2006-07-20
Hi all,
       I had a partition in /dev/hdb7 which was mounted on /media/hdb7 now by mistake I unmounted it. This is the result from mount -l

/> dev/hdb3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hdb5 on /media/hdb5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hdb6 on /media/hdb6 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hdb8 on /media/hdb8 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

Now how can I remount the partition with the same things as the others say hdb8, Thnx in advance.

---

### Post by philippe_carlo on 2006-07-20
man mount

---

### Post by goobers on 2006-07-20
try **mount /dev/hdb7 /media/hdb7**

---

### Post by goobers on 2006-07-20
or you could try doing it through system/administration/disks

---

### Post by Ramses de Norre on 2006-07-20
If it's in fstab: ```
sudo mount -a
```

If not: ```
sudo mount /dev/hdb7 /media/hdb7 -t ntfs -o rw,nls=utf8,umask=007,gid=46
```

---

### Post by goobers on 2006-07-20
oops yeah, sorry, forgot to put in the filesystem... follow Ramses de Norre's way :S

---

### Post by ShirishAg75 on 2006-07-20
Thnx guys, I didn't have to do anything, a simple reboot was all it required. Most probably it would have done the mount -a command. Am I right?

---

### Post by endfx on 2006-07-20
Yes, you are right.
If you rebooted and it mounted again on its own, then a "sudo mount -a" would
have fixed it for you.

---

