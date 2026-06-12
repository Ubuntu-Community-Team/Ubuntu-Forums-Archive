---
title: "USB partition table"
date: 2005-11-13
forum: Desktop Environments
---

### Post by mrshish on 2005-11-13
I think I somehow killed the partition table on my USB drive. I copied a file to it and moved the USB drive to a windows machine. Windows said it didn't have a valid formate. When I moved the drive back it back to Ubuntu it won't mount. If I try to mount the drive it says that the UDI is not a mountable partition. I tried using parted but if I run a command like CHECK it says: 

Error: Unable to open /dev/sda – unrecognized disk label. 

Normally I would just blow the drive away and start over but there are a couple files I need off it first. Any help would be appreciated.

---

### Post by nagilum on 2005-11-14
Maybe there are no more partitions on the drive. Have you tried to mount /dev/sda directly?

---

### Post by mrshish on 2005-11-14
I tried it but no luck...

---

### Post by nagilum on 2005-11-15
Can fdisk print the partition table of your drive? Run 'fdisk /dev/sda' and enter the command 'p'.

---

