---
title: "dpkg erorr when trying to update system [8.04]"
date: 2009-01-25
forum: General Help
---

### Post by Fredrik_b on 2009-01-25
Hi Just suddenly one nigt my computer started to act up

I could not connect via nx Server and on the computer itself i could not update the system.

When updating I get asked to type 

```
sudo dpkg --configure -a 
```

After a typed that I got an error saying some file was missing in /usr/sbin/mkinitramfs/ I dl a .tar file with some files (
getopt1.c  getopt.c  getopt.h) who someone said belonged there) and created this catalog.

Now I get this error when running sudo dpkg --configure -a 



```

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
/usr/sbin/update-initramfs: 516: mkinitramfs: Permission denied
update-initramfs: failed for /boot/initrd.img-2.6.24-22-generic
dpkg: subprocess post-installation script returned error exit status 127
ad@server:~$
__
```

Anyone know how to fix this?

---

