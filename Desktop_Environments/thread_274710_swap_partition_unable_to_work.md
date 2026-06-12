---
title: "swap partition unable to work"
date: 2006-10-10
forum: Desktop Environments
---

### Post by baosheng on 2006-10-10
Hi guys,

suddenly, I found I have no swap partition available on my computer.
Can any one help on solving this problem? Thanks.

here is the result of free
forrest@orioleQ:~$ free
             total       used       free     shared    buffers     cached
Mem:        708748     467480     241268          0       9812     291428
-/+ buffers/cache:     166240     542508
Swap:            0          0          0

I got a snapshot from "Disc" program.
[http://www.flickr.com/photos/forrestbao/266000808/](http://www.flickr.com/photos/forrestbao/266000808/)
[IMG]http://static.flickr.com/80/266000808_14bcaaac42.jpg?v=0[/IMG]


And here is my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /forrest        ext3    defaults        0       2
/dev/hda3       swap            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

This is my "mount" result
forrest@orioleQ:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-686/volatile type tmpfs (rw)
/dev/hda2 on /forrest type ext3 (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=forrest)

---

### Post by mssever on 2006-10-10
What is the output of ```
sudo swapoff -av; sudo swapon -av
```

---

### Post by baosheng on 2006-10-10
forrest@orioleQ:~$ sudo swapoff -av; sudo swapon -av
Password:
swapoff on /dev/hda3
swapon on /dev/hda3
swapon: /dev/hda3: Invalid argument

---

### Post by mssever on 2006-10-10
I have no idea what that invalid argument error is about. Too bad it isn't more verbose. I did notice that the swap line of your fstab is a little different than mine. Here's mine: ```
/dev/hda2       none            swap            sw                  0       0
```
I don't know whether this will make any difference, though.

---

