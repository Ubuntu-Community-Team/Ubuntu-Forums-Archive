---
title: "hotplugging of usb memory stick not working"
date: 2007-04-20
forum: Desktop Environments
---

### Post by Bloch on 2007-04-20
I upgraded to Feisty last night, all working well except . . . 

Neither my external hard drive nor any of my memory sticks are automatically mounted.

In Dapper, whenever I plugged in a memory stick or switched on the external hard drive, the nautilus window would pop up seconds later.

The devices are detected and listed in 
```
sudo fdisk -l
```

and by lsusb as 
```
Bus 004 Device 003: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
```

and I can moiunt them manually (after creating the directory /media/usb_stick) with e.g. 
```
sudo mount -t vfat /dev/sdb1 /media/usb_stick 
```


How can I get my hotplugging back?

---

### Post by oiper on 2007-04-21
I too am having this problem. Any luck?

---

### Post by dcstar on 2007-04-22
In a terminal, when you plug in the device run:
```
dmesg
```
and post the last few lines.

Make sure that System-Preferences-Removable Drives-Removable Storage has the first items two ticked.

---

