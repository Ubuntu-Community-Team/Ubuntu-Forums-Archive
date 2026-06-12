---
title: "Two strange problems with XFCE..not in Gnome..."
date: 2008-12-04
forum: Desktop Environments
---

### Post by night-wing on 2008-12-04
Hello.

I use Xubuntu this time and like it more, than Ubuntu with the Gnome-Desktop, because it's very smooth on my notebooks.

But I recognized two strange problems in XFCE, which both not occured in Gnome with Nautilus...

- On one of the notebooks I have two internal HDs. On the second
  one there is Windows Vista installed (NTFS). But in Thunar I 
  can't see them. In Nautilus I can. Of course, I can mount them
  manually, but this is not necessary when using Gnome.
- I use different USB Sticks and SD - Cards and external HDs for
  Backup and digital Pictures. The USB Sticks make no problem
  when I try to mount or to dismount them in thunar. But both the
  SD Cards and also the external HDs (FAT32 or NTFS) can be
  mounted - but not dismounted in thunar! I always get an error,
  that there is a "wrong ioctl" and the drive can not be ejected.
  In Gnome there is no problem with this at all!

Can someone give me a hint? I really searched for nearly a week
about these problems and didn't get a clue.

Thanks.

night-wing

---

### Post by Toet on 2008-12-04
Nautilus uses it's own software to mount and unmount drives. So the fact that it does work in Gnome and does not work in XFCE is not related.

The problem you have can be discribed more simple imho:

Drives not mounting automatically in Thunar and dismounting gives IOCTL error.

---

### Post by Toet on 2008-12-04
I found this on automounting:

In order for that to work, you need to make sure that Thunar volume management is turned on. In thunar, edit preferences, click on Advanced, and make sure that enable volume management is checked. That's the mechanism by which XFCE automatically mounts usb flash drives.

In this thread:

[http://ubuntuforums.org/showthread.php?t=899287](http://ubuntuforums.org/showthread.php?t=899287)

---

### Post by Toet on 2008-12-04
Can you start Thunar from a terminal (cli) and post the exact error it gives when unmounting a device?

---

### Post by medic2000 on 2008-12-04
Also when you are using thunar volume management, dont forget to add "#" in front of your cd and dvd devices in fstab. Otherwise it conflicts and you will face with a not automounting cds or/and dvds.

---

### Post by night-wing on 2008-12-04
Thanks.

I'll try this today after work and will post the results and the error log.

---

### Post by night-wing on 2008-12-04
Ok. First. The fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=024ec113-7c8d-4fdd-94bd-5d81d59e1a07 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1163ca09-3d37-4f4f-a39b-d7c7ab50bc56 /home           ext3    relatime        0       2
# /dev/sda2
UUID=77ca4394-e6b6-4e2a-bddc-339ae5cb5878 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


What I tried...
1. Activation of automatic device management in thunar
   didn't work for me. The external usb and the sd card were mounted
   automatically but I still can't dismount them in thunar.
2. The xfce-mount-plugin
   didn't work. It shows only the drives in the fstab. All usb drives
   are in the mtab. There are not shown in this tool...
3. gnome-volume-manager
   I wanted to install and try it. But it wants to install half of
   gnome as depencies. This is not what I want.

The correct error message is

"/usr/bin/eject: unable to eject, last error: Inappropriate ioctl for device"

---

### Post by Toet on 2008-12-04
Interesting might be:

[http://www.linuxmint.com/forum/viewtopic.php?f=49&t=17717](http://www.linuxmint.com/forum/viewtopic.php?f=49&t=17717)

---

### Post by night-wing on 2008-12-05
Thanks.
I'll try this after work.

---

### Post by night-wing on 2008-12-05
I'm sorry to say, that this doesn't work for me (pmount/pumount) :-(

---

### Post by morgengenuss on 2008-12-09
ok, for your internal ntfs-partition adding it to fstab should do the trick (but i guess you already figured that out).

for unmounting/ejecting your external drive (btw are you using 8.04 or 8.10?) you could use sdparm.

e.g.
```
sdparm --command=stop /dev/sdb1
```
(where sdb1 is the device-name of your external drive, you can easily find out the device name of a mounted device with the "mount" command.)
this command spins down your harddrive, so that it is safe to remove.

regarding pumount: would you mind posting your terminal output?

---

