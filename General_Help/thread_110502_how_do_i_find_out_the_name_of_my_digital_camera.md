---
title: "how do i find out the name of my digital camera?"
date: 2005-12-30
forum: General Help
---

### Post by ren wins on 2005-12-30
i want to eject it, but i dont know what to call it?
if i try to unmount it from the desktop icon (right click > unmount) i get an error saying it cant unmount

lsusb returns 
> laserwolf@violet:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybe rshot/Mavica Digital Camera
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


mount returns
> 
laserwolf@violet:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/hda1 type ntfs (rw)
/dev/hdb6 on /media/hdb6 type ntfs (rw)
/dev/hdb7 on /media/hdb7 type ntfs (rw)
/dev/hdb8 on /media/hdb8 type vfat (rw)
/dev/hdb9 on /media/hdb9 type vfat (rw)
/dev/hdb8 on /media/static type vfat (rw,umask=000)
/dev/hdb9 on /media/support type vfat (rw,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)


i tried sudo umount /proc/bus/usb ... but that didnt do anything that i noticed, except remove "usbfs on /proc/bus/usb type usbfs (rw)" from the mount list

thanks in advance

---

### Post by sciurus on 2005-12-31
All I see are hard drive partitions (why so many, if I may ask) and normal system things. For a camera I would expect something like */dev/sda1 on /media/something type vfat (rw,noexec, etc...)*

---

### Post by ren wins on 2005-12-31
i have so many b/c i have a 200gb HD and it seemed like a good idea to keep music on one partition, movies on another, pictures on a third and a 4th for pack-ups of windows and linux
plus partitions for windows (hda1, which i'll probably partition up sooner or later and put another linux system on for laughs) and 2 partitions for linux

---

