---
title: "GRUB error 17"
date: 2009-06-18
forum: General Help
---

### Post by desperateone on 2009-06-18
This morning, I launch my EEEPC and I get a GRUB 17 error. So I boot from a pendrive and try to mount the /dev/sdb1 (where my system is), but I get the standard mount error message (unknown fs, blah, blah). So I grab gparted, but it says that the file system on /dev/sdb1 is unknown, and fsck says ``Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1\Could this be a zero-length partition?''. I don't have anything especially important on the drive, but it would be nice if I could salvage the preference files before OS reinstall, could that be done in any way?

---

### Post by quinntar on 2009-06-18
Hi, as for me when I used to have this I reinstalled my machine but you can try a solution that worked fine for me once or twice till my last re install.

Go download SUPER GRUB DISK
Burn it on a CD or put it on a usb stick then you should be abble to get your Grub work again and you should be able to boot your eeepc.

Find the super grub disk here : [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I hope it will help you.:KS

Quinntar

---

### Post by metalf8801 on 2009-06-18
You can make a live SUPER GRUB DISK flash drive quickly and easily using UNetbootin on Windows or Ubuntu 
you can download it here [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
or you can get using Add/Remove 

here some more info on fixing grub error 17 
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

I hope that stuff helps 
Dan

---

### Post by desperateone on 2009-06-18
> **metalf8801 said:**
> You can make a live SUPER GRUB DISK flash drive quickly and easily using UNetbootin on Windows or Ubuntu 
you can download it here [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
or you can get using Add/Remove 

here some more info on fixing grub error 17 
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

I hope that stuff helps 
Dan

I saw that thread earlier, skimmed it, but none of the suggested things worked/applied to me, so I gonna reinstall the OS.
Thanks for the SGD, I'll check it out.

---

