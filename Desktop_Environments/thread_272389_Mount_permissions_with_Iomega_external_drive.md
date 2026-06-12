---
title: "Mount permissions with Iomega external drive"
date: 2006-10-06
forum: Desktop Environments
---

### Post by ejardim on 2006-10-06
Hi,

I have an USB Iomega external drive 500GB. I've created 2 partions, one FAT32 with 30GB and one ReiserFS with 460GB.

When I plug it both are mounted but while the FAT32 gets the correct permissions so that my user can rw it, the ReiserFS is mount with root ownership and I can not use my own user to rw it.

I've made two attempts to deal with this
1) changed the owner of the /media/EJBACKUP 
2) inserted a new line in fstab and pmount.allow so that my user could mount it

but I did not succeed ... any ideas ? 

Thanks

EJ

The outputs of ls and mount 

ernesto@gandalf:~/tmp$ ls -l /media/
total 28
lrwxrwxrwx  1 root    root        6 2005-07-07 12:50 cdrom -> cdrom0
drwxr-xr-x  2 root    root     4096 2005-07-07 12:50 cdrom0
drwxr-xr-x  2 root    root     4096 2005-07-07 12:50 cdrom1
drwxr-xr-x  6 root    root      128 2006-10-06 10:53 EJBACKUP
lrwxrwxrwx  1 root    root        7 2005-07-07 12:50 floppy -> floppy0
drwxr-xr-x  2 root    root     4096 2005-07-07 12:50 floppy0
drwx------  4 ernesto ernesto 16384 1970-01-01 01:00 NEW VOLUME
ernesto@gandalf:~/tmp$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-686/volatile type tmpfs (rw,mode=0755)
/dev/sda4 on /home type ext3 (rw)
/dev/sda2 on /usr/local type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb2 on /media/EJBACKUP type reiserfs (rw,nosuid,nodev)
/dev/sdb1 on /media/NEW VOLUME type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

---

