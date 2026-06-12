---
title: "Disks not showing when on battery"
date: 2008-02-27
forum: Desktop Environments
---

### Post by parkland on 2008-02-27
It seems that if i'm running on battery power, or charging the battery, my "windows" volume dosnt show up !?!?!

My dvd-rom, and ubuntu volume shows up, but the windows one doesnt.

WTF?!??!?!?!?!

---

### Post by bazzawill on 2008-02-27
Not sure why it would differentiate when running on battery/charging but try to mount the drive in a shell use
```
sudo fdisk -l
``` this will print a list of you're hardrive volume find the hpfs/ntfs volume this will be your windows drive make note of the device which will be something like /dev/sda5 then use 
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g (windows device) /media/windows
```
if there are problems post the output

---

