---
title: "Mount Fat32 Drive in Ubuntu"
date: 2006-06-29
forum: Desktop Environments
---

### Post by masood on 2006-06-29
Hi, i am new new ubuntu user. How to mount fat32 drives in Ubutu?

---

### Post by Maggot on 2006-06-29
sudo mount -t vfat /dev/sda1 /media/windows

Replace sda1 with whatever partition your windows is on.  Make sure your /media/windows directory exists, if not create it: sudo mkdir /media/windows or where/whatever you want it to be.

---

### Post by Luke771 on 2006-06-29
```
sudo mount -t vfat /dev/hdaX /<path>/<to>/<mount point>
```

Where hdaX is your FAT32 partition (hda2, hda5, whatever) and the path to mount point is path to a directory used to mount the partition (duh)

Anyway, as I recently discovered, there are Ext2 drivers for Windows, so we don't need Fat32 any more ;-)

---

### Post by solarwind on 2006-06-29
[QUOTE=Maggot]sudo mount -t vfat /dev/sda1 /media/windows

Replace sda1 with whatever partition your windows is on.  Make sure your /media/windows directory exists, if not create it: sudo mkdir /media/windows or where/whatever you want it to be.[/QUOTE]

Also, if you don't know what your drive is, do this:

sudo fdisk -l /dev/hda

replace /dev/hda with your drive device and check your partition with the fdisk output.

---

### Post by Maggot on 2006-06-29
[QUOTE=Luke771]Anyway, as I recently discovered, there are Ext2 drivers for Windows, so we don't need Fat32 any more ;-)[/QUOTE]
That's what I thought but wasn't sure :D

---

### Post by glotz on 2006-06-29
Or system > admin > disks > select the disk and partition > mount (will be mounted to /media/)

---

### Post by Luke771 on 2006-06-29
oh yeah?
I didn't know that. I guess I should check my menus out more closely.

Must be like I heard somewhere " 'Ubuntu' is an ancient African word meaning 'can't install Debian' "

---

### Post by glotz on 2006-06-29
[quote="Luke771"]Must be as I heard somewhere " 'Ubuntu' is an ancient African word meaning 'can't install Debian' "[/quote]
HAHAHA! :lol:

---

