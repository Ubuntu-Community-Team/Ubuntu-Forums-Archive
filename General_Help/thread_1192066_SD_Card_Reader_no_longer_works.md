---
title: "SD Card Reader no longer works"
date: 2009-06-19
forum: General Help
---

### Post by jimasbille on 2009-06-19
In Ubuntu 8.04 I can no longer use my Standard Microsystems Corp. 9-in-2 Card SD Card Reader that is in my Dell Ultrasharp 2407wfs monitor.

Help!  This is the only way I can get EXIF data into Picasa.  Here is some useful information.

lsusb:
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 015: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 007 Device 014: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 007 Device 013: ID 0424:2602 Standard Microsystems Corp. 
Bus 007 Device 012: ID 0424:2502 Standard Microsystems Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 413c:2105 Dell Computer Corp. 
Bus 003 Device 005: ID 413c:3012 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 03f0:4f11 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=00016a28-e978-480a-bce6-75afa6b8d09f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a57c3130-723f-41bf-baac-463216470eb7 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
# 1001 is the USB group
none /proc/bus/usb usbfs devgid=0100,devmode=664 0 0

/dev/sdb1  	/media/TREKSTOR  vfat noauto,async,rw,nosuid,nodev,umask=000,uid=1000 0 0

mount 'l
/dev/sda3 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
none on /proc/bus/usb type usbfs (rw,devgid=0100,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdd1 on /media/TREKSTOR type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush) [TREKSTOR]

---

