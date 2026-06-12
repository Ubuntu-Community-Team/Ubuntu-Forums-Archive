---
title: "No more auto-mount on CD/DVD reader"
date: 2007-10-15
forum: Desktop Environments
---

### Post by EvilAngel on 2007-10-15
Hi all,

I am with Kubuntu 7.04 with AMD64.

I don't know why but I don't have auto-mount anymore on my CD/DVD player.
When I am inserting a media in the reader, nothing is appearing on my desktop.

If i browse and I open /edia/cdrom0, it is empty inside. :confused:

Here is my /etc/fstab file:
```
toto@TEST:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8e22dc21-f9f7-447f-b7e9-c8eb269dca98 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=babdcc5d-6a4d-4623-b022-3d95da3048d2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#disque windows
/dev/sdb1       /media/data     vfat    rw,user,auto,exec,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850    0    0
toto@TEST:~$
```And when I inser a CD/DVD in the reader and I try to make an fdisk on it, fdisk is then blocked:
```
toto@TEST:/dev$ fdisk /dev/hda


```Any idea ?
Thanks

---

### Post by TeaSwigger on 2007-10-16
> **EvilAngel said:**
> Hi all,

I am with Kubuntu 7.04 with AMD64.

I don't know why but I don't have auto-mount anymore on my CD/DVD player.
When I am inserting a media in the reader, nothing is appearing on my desktop.

If i browse and I open /edia/cdrom0, it is empty inside. :confused:

Here is my /etc/fstab file:
```
toto@TEST:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8e22dc21-f9f7-447f-b7e9-c8eb269dca98 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=babdcc5d-6a4d-4623-b022-3d95da3048d2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#disque windows
/dev/sdb1       /media/data     vfat    rw,user,auto,exec,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850    0    0
toto@TEST:~$
```And when I inser a CD/DVD in the reader and I try to make an fdisk on it, fdisk is then blocked:
```
toto@TEST:/dev$ fdisk /dev/hda


```Any idea ?
Thanks

I thought /dev/hda was a (now outdated) name for a hard disc. What would one use fdisk for in linux, and on an optical drive? I'm no expert though. At any rate try replacing /dev/hda with /dev/scd0 and/or /dev/sr0 as the device location for your optical drive and reboot.

---

### Post by D-EJ915 on 2007-10-16
nautilus stopped showing things when I plugged them in to the USB and didn't show CDs either, I restarted and it then worked fine.  *shrug* worth a try at least if it worked before but now doesn't.

---

