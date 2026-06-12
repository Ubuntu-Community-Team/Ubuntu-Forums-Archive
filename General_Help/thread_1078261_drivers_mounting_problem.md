---
title: "drivers mounting problem"
date: 2009-02-23
forum: General Help
---

### Post by bertolo on 2009-02-23
hi!during past 3 days i was unable to mount my usb pen in my ubuntu 8.04. When i try to access My Computer it says that my computer it's a unknown location.
:/

---

### Post by plucky on 2009-02-23
With the stick out open a terminal and ```
lsusb
``` then plug in the stick and ```
lsusb
sudo fdisk -l
``` and post output if any difference.(use lowercase L not a 1)

Good Luck

---

### Post by bertolo on 2009-02-23
i have no way to pass output ou lol, it's it another pc without internet. the output was something like this:
before:
bus5 ID 00000
bus4 ID 00000
...3 ID 00000
...2 Mouse
...1 ID 00000
...0 ID 00000
after:
bus5 FLASH PEN 2GB (omfg my pen is only 1 gb ROTFL)
bus4 ID 00000
...3 ID 00000
...2 Mouse
...1 ID 00000
...0 ID 00000

i think there is some bug here, i plugged 2 usb pen disks in my pc, and lsusb showed:
bus5 FLASH PEN 2GB (omfg my pen is only 1 gb ROTFL)
bus5 ID 00000
bus4 ID 00000
bus4 ID 00000
...3 ID 00000
bus3 2nd usb pen.
...2 Mouse
bus2 ID 00000
...1 ID 00000
bus1 ID 00000
...0 ID 00000
bus0 ID 00000

---

### Post by plucky on 2009-02-23
What about ```
sudo fdisk -l
```

Also if you need to transfer the file over to another pc, you can pipe the output to a file with ```
sudo fdisk -l > fdisk.txt
``` will create a file fdisk.txt which you can copy to a pen drive to copy to the forum.


The pen drive that is not working does it work on a Windows system?

Does the other pen drive work?

There is a possibility that it wasn't dismounted properly in windows and the file system is un-clean,which would stop it mounting in linux.

Plug it into a windows machine and un-mount it properly and then try it on linux again.

---

### Post by bertolo on 2009-02-23
no there is no way to get the output...maybe printing lol.
i can't access my computer either

---

