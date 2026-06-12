---
title: "Kubuntu won't load!!!"
date: 2005-06-25
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-25
I must have phucked up my partition i'm afraid.  I ran partition magic to take some of the free space from my windows partition and expand the linux partition to take it.  Well i did so, and when i rebooted and got to the GRUB loader, I selected the Kubuntu choice, and got this error:

root (hd0, 4)
     Filesystem typs is fat, parition type 0xb
kernel    /boot/vmlinuz-2.6.10-5-386 root = /dev/hdc5 ro quiet splash

Error 15:  File not found.


Did i lose it all guys?  Or is there a solution?  

PS i'm on a laptop dual booting.

Thanks

---

### Post by fdoving on 2005-06-25
[QUOTE=vtechstu]I must have phucked up my partition i'm afraid.  I ran partition magic to take some of the free space from my windows partition and expand the linux partition to take it.  Well i did so, and when i rebooted and got to the GRUB loader, I selected the Kubuntu choice, and got this error:

root (hd0, 4)
     Filesystem typs is fat, parition type 0xb
kernel    /boot/vmlinuz-2.6.10-5-386 root = /dev/hdc5 ro quiet splash

Error 15:  File not found.


Did i lose it all guys?  Or is there a solution?  

PS i'm on a laptop dual booting.

Thanks[/QUOTE]
 Did you make a new partition? Can you explain the partitioning on your disk?

---

### Post by vtechstu on 2005-06-25
Alright before i ran partition magic, i had a partition for windows, and one for linux.  I needed more space, so i shrunk the windows partition, since it had lots of extra space.  The extra space i then had the linux partition take into itself.  So windows partiion was smaller, and the linux one got 5 more gigs.  Windows works fine, grub loader doesn't see linux I guess. So, yea. Thats about it.  Thanks

---

