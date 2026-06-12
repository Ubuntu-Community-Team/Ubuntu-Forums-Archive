---
title: "Read-Write options in fstab"
date: 2005-02-26
forum: Desktop Environments
---

### Post by whackker on 2005-02-26
I'm fairly new to Ubuntu, and I am having some difficulties getting a media hard drive to have read-write access. I can view the hard drive, and I can do everything but write to it. I have messed around with fstab enough so that I don't even know what to try anymore. Any suggestions?

---

### Post by alastair on 2005-02-26
Best idea - scan the man page for mount - there are various universal options, and file system specific ones.

man mount

I think you can also use the gnome help browser for man pages.

Interresting information to see :

- relevant fstab line
- output of "mount" command
- ls -l /mnt   (or wherever the directory is - showing mount point)

---

### Post by whackker on 2005-02-26
/dev/hdd1       /mnt/Media      vfat    noexec,umask=003,gid=100  0 0


~ $ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hdd1 on /mnt/Media type vfat (rw,noexec,nosuid,nodev,umask=002)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdb on /media/cdrom0 type udf (ro,noexec,nosuid,nodev,user=mwaecker)


~ $ ls -l /mnt
total 36
drwxr-xr-x    2 root     root         4096 2005-02-21 14:54 Filez
drwxrwxr-x   13 root     root        32768 1969-12-31 19:00 Media


The one I'm trying to get accress to is 'Media,' which is hdd1,  and not 'Filez' :ashamed:

It shows in the mount output that Media has rw access, but I still can't create folders, or delete things in it.

---

