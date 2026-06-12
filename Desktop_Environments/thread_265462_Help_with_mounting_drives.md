---
title: "Help with mounting drives"
date: 2006-09-26
forum: Desktop Environments
---

### Post by st0ney on 2006-09-26
I am trying to install 2 identical 400GB seagate drives.  I have them all hooked up correctly and formated it ext3 using gparted making them hde and hdg.  I made 2 different mount points, one for each drive, at /media/storageA and /media/storageB.  I've edited the fstab file to look like > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hde1       /media/storageA  ext3    defaults        0     0
/dev/hdg1       /media/storageB  ext3    defaults        0       0


When I saved that and run mount I get this:  > /dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hde1 on /storage type ext3 (rw,errors=remount-ro)
/dev/hde1 on /storage type ext3 (rw)


When I open up "computer" under "Places"  I can only see 1 drive and I can open it but there is a lost and found folder in there.  Sorry for the n00bness but I can't figure out what is going on.  Any help would be appreceiated.

Thanks.

---

### Post by jISh on 2006-09-26
How are you mounting the drive?
sudo mount /dev/hde1 /mount/storageA
Is how you should be doing it for the first drive, as an example.

---

