---
title: "Hey, where's my USB drive?"
date: 2006-05-09
forum: Desktop Environments
---

### Post by Zorb on 2006-05-09
``sudo mount /dev/sda1 .Mount'' gives me "You have to specify filesystem type" messages.

ivman and that g-v-m don't mount anything but don't report any errors. 

An ls of /dev/ reveals nothing named /dev/sdxx . 

So I'm really pissed off.

Any suggestions? Spontaneous filesystem corruption, perhaps?

---

### Post by louis_nichols on 2006-05-10
I know this is obvious, but did you try mentioning the fstype, as it asks? I'm guessing it is vfat.

---

### Post by seatea on 2006-05-10
I had a problem develop with a usb drive failing to mount and corrected it by reinstalling gnome-volume-manager and HAL. You might try that.

---

### Post by red_shrike on 2006-05-10
Go to /etc/fstab and add /dev/sda1 /media/sda1 auto 0 0 (with tabs in between) If this doesnt work, change sda1 to 2, 3, 4, or what works (shouldnt be more than 8. Run mount /dev/sda1 and there you go

---

### Post by towsonu2003 on 2006-05-10
though it's usually /dev/sda1, attach the usb and check where it is with ```
sudo fdisk -l
```
if it doesn't list a new "partition" but only your harddisk, check what happened with ```
dmesg | tail
``` or ```
dmesg | less
```

than the previous poster gives you what to do with the /etc/fstab file :)

---

### Post by red_Marvin on 2006-05-10
Try
*sudo mount -t vfat [your directoryandmountpoint here]*
If it doesn't work, try
*sudo mount -t auto [your directoryandmountpoint here]*
If that doesn't work do this (to see if you have the same problem as me):
*ls /dev/sda**
and post the output

---

### Post by red_shrike on 2006-05-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           reiserfs defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults        1       0
/dev/hda5       /media/hda5     vfat    defaults        1       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   iso9660    user,auto    0       0
/dev/hdc        /media/cdrom1   iso9660    user,auto    0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/sda1     auto    rw,user,auto     0       0


This is my fstab, I have added the last line and it works now. Try modelling it by this.

---

