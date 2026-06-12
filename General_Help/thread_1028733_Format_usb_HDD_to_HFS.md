---
title: "Format usb HDD to HFS"
date: 2009-01-02
forum: General Help
---

### Post by poo_22 on 2009-01-02
I need to format my external hard drive to the hfs filesystem (for use with ps3) and the option in gparted is greyed out. Does anyone know how i can do this?

Also i would like to know if ubuntu can mount a drive formatted in hfs.

---

### Post by fbjoey on 2009-01-02
I don't know about mounting the drive in ubuntu but can't you use your ps3 to format the drive?

---

### Post by jbrown96 on 2009-01-02
You just need the packages to create/mount hfs. I'm not sure exactly which package you need, but these three will solve the problem. ```
sudo apt-get install hfsutils hfsplus hfsprogs
``` Mounting is just as easy as with any other drive. It will appear on your desktop and in Places.

Edit: Unless you are using files that are over 4GB or the drive is very large, you should use vfat (fat32).

---

