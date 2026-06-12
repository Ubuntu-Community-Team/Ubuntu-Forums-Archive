---
title: "mount problems"
date: 2006-05-11
forum: Desktop Environments
---

### Post by amimanou on 2006-05-11
Hello, 

When I plug an USB Device the automonter pmount fails.

1] I plug a Pen Drive
2] The mount bar shows the option to mount the device (twice)
3] I mount one and it mount only the filesystem (some files from the penDrive that I have never seen) but it still appears the option mount anyway
4] I have an error window

--- some msg that can be usefull to solve the problem ---

manou@acad4143act:~$ mount
/dev/sda9 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/sda3 on /boot type ext3 (rw)
/dev/sda7 on /home type ext3 (rw)
/dev/sda8 on /tmp type ext3 (rw)
/dev/sda6 on /usr type ext3 (rw)
/dev/sda5 on /var type reiserfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

manou@acad4143act:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /boot           ext3    defaults        0       2
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda8       /tmp            ext3    defaults        0       2
/dev/sda6       /usr            ext3    defaults        0       2
/dev/sda5       /var            reiserfs defaults        0       2
/dev/sda10      none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


manou@acad4143act:~$ mount /dev/sda1 -t vfat /media/usbDev/
mount: sólo el usuario root puede efectuar esta acción
manou@acad4143act:~$ sudo mount /dev/sda1 -t vfat /media/usbDev/
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Can somebody help me to solve the problem, please?

PD: I have try to check/uncheck the options in Preferences/External Devices related to USB devices.

Thank you very much for your time.

·_· manou

---

