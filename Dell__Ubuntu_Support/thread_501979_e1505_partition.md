---
title: "e1505 partition"
date: 2007-07-16
forum: Dell  Ubuntu Support
---

### Post by johnn1949 on 2007-07-16
I have a Dell E1505 w/intel t7200 chip.  Ati X1400 graphics.  The live cd runs fine.  I have installed dapper and feisty in other computers with a single primary partition.  I think the Dell has 3 primary partitions and one logical.  I want to install Ubuntu into 20 gigs of the c: partition.  The unknown partition is the recovery dell section.  Will the alternate cd install correctly, using largest free space on disk? Will the EISA partition still work with xp ( I don't know what that does)?

---

### Post by terrapisces on 2007-07-16
The EISA partition is the 32bit Diags, it should still work as it is accessed by BIOS not OS. What I suggest is to resize the NTFS part and use the freed space from there. Installing Ubuntu will change the MBR, but GRUB will have the entry for Windows.

---

### Post by johnn1949 on 2007-07-16
Thanks for the info on EISA.  I'm a little unsure of install ,but I think I will try it and see.

---

### Post by 5-HT on 2007-07-16
I had to add a grub entry for the diagnostic partition to be able to boot into it (even from the bios option).
Just edit the partition to your particular situation if needed:
```
title         Dell Diagnostics
rootnoverify    (hd0,0)
chainloader     +1 
```cheers,

---

### Post by johnn1949 on 2007-07-16
Thanks 5-HT,

Can you give me a little more info on the Grub entry?  I really don't know how or where to edit it or how to figure out what my situation is.

---

### Post by strabes on 2007-07-17
The grub configuration file is /boot/grub/menu.lst. Towards the bottom of the file are the grub boot entries. Here's my windows one:

> title		Windows XP LOL!!!!!!!!!!!!
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by 5-HT on 2007-07-18
> **johnn1949 said:**
> Thanks 5-HT,

Can you give me a little more info on the Grub entry?  I really don't know how or where to edit it or how to figure out what my situation is.

      strabes covered it nicely. One little point though: you should append the entry to the bottom of the file, after the ### END DEBIAN AUTOMAGIC KERNELS LIST section because everything contained within that section will be automatically updated when you update your kernel (a nice touch by Debian!) and your custom entries could disappear. Anything added after that line will not be touched.

Post back if you have any problems.
cheers,

---

### Post by strabes on 2007-07-18
Something I forgot to mention: You may have to change the 0 in the "root (hd0,0)" part to something else, depending on which partition you want that GRUB entry to refer to. "0" refers to the first partition on the disk, "1" refers to the 2nd, "2" refers to the third, etc.

---

