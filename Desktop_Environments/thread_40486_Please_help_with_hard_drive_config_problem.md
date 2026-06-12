---
title: "Please help with hard drive config problem"
date: 2005-06-09
forum: Desktop Environments
---

### Post by makoto on 2005-06-09
Hi, if anyone could help me a bit with this I would greatly appreciate.
(Btw :  I a noob to Linux, installed it for the first time 2 days ago)

I have two drives, the master (hda1) is ext3 and the slave (hdb1) was NTFS.  In order to be able to write to the slave, I formatted it to FAT32. with  sudo  mkfs.vfat -F 32 /dev/hdb1.  The drive seems to be mounted but when I try to create a folder in it, the folder appears in media:/hda1/drive2 instead of hdb1/ .

Here is the mount input : 
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdb1 on /drive2 type vfat (rw,iocharset=iso8859-1,codepage=850,umask=0000)

Here is my fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /drive2         vfat    iocharset=iso8859-1,codepage=850,rw,umask=0000                                          0       1


I can also post the procedure Iused to format the drive as I have it written down. (In a modified "How to" kind of format.


Any help would be appreciated. Thanks

---

### Post by makoto on 2005-06-09
problem fixed on irc....

---

