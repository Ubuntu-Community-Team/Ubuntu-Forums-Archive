---
title: "How do you format a USB stick?"
date: 2008-08-20
forum: Desktop Environments
---

### Post by bliffle on 2008-08-20
I have a 2gb USB memory stick here that seems to have a messed up file system. In spite of the care I took when deleting a file, the space was not given back to the USB filesystem, even emptying the trash, doing ejects, etc.

So it only shows 50mb as available. So I deleted everything, hoping that might break the logjam, but no luck. So I figured I'd just 'reformat' the USB like we used to do with floppies when that happened, but I don't know what utility to use, or even if it can be done with a USB.

Anyone have experience with re-formatting a USB, or  otherwise rectifying the file system?

---

### Post by SuperSonic4 on 2008-08-20
Use gparted or any other like partition editor, just like you would with a hard drive

---

### Post by linuxguymarshall on 2008-08-20
There is some way using fdisk but honestly I just use GParted

---

### Post by Potatoj316 on 2008-08-20
you can use mkfs.vfat to make a filesystem on it (which would be formating) but I dont know how to do it.

---

### Post by bliffle on 2008-08-20
Looks like I got it done with gparted.

Thanks, guys.

---

