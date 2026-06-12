---
title: "Gnome computer browser hide some devices"
date: 2007-11-01
forum: Desktop Environments
---

### Post by EdeCaluwe on 2007-11-01
My computer contains 3 sata disks with several partitions. Two of these disks compose a fake raid array. 

The gnome computer browser is ' smart' enough to list all partitions in /dev even without them being listed in fstab or being mounted. This is a very nice feature for usb disks etc. However for permanent storage devices I would like to decide myself which device / partitions are listed and which not. How can I do this ? Of course I do want to keep all other automatic mounts for usb disks etc.

For example in my case I have installed the dmraid package. Therefore I want to mount the /dev/mapper mapped devices and not the individual drives. However the Gnome browser automatically adds these individual devices to the list and these are obviously not mountable. How can I disable this ?

---

