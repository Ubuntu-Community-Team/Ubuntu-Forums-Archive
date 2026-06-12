---
title: "mounting problem"
date: 2008-02-04
forum: Gaming &amp; Leisure
---

### Post by jeddah_fbi on 2008-02-04
i have an iso game and am trying to mount it using Gmount-iso by following the instructions in this guide [http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

but i get an error like the attached pic

what to do :(

---

### Post by aphirst on 2008-02-04
It's most likely that it isn't a standard ISO format.
1)Try burning it to a disc, or md5sum it if it was dloaded off the web

2) try using the command, 
```
sudo mount file.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0
```
to manuallly mount it.

---

### Post by markharding557 on 2008-02-08
> **jeddah_fbi said:**
> i have an iso game and am trying to mount it using Gmount-iso by following the instructions in this guide [http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

but i get an error like the attached pic

what to do :(

try changing the mount point to something like /mnt thats not in the same place as your iso

---

