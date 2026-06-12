---
title: "Booting via GRUB"
date: 2009-06-10
forum: Desktop Environments
---

### Post by Geffers on 2009-06-10
I have a dual boot Acer Aspire One system booting URM and the original OS Linpus.

Using gparted I copied the entire URM partition to an 8GB usb key. It is not booting so I am suspecting a GRUB problem.

Naturally as it was a partition copy the original GRUB folder and menu.lst file is all present.

I am a wee bit confused now as to what I need to alter, I am thinking it may be the menu.lst file.

Any pointers appreciated.

Geffers

---

### Post by Person_1873 on 2009-06-10
have you made the partition bootable? and have you installed GRUB onto the drive from another machine?

---

### Post by Geffers on 2009-06-10
> **Person_1873 said:**
> have you made the partition bootable? and have you installed GRUB onto the drive from another machine?

Using gparted I selected the boot option.

I did not install GRUB, it was a partition copy so what was on the original partition is on the new one.

Geffers

---

### Post by Entropy_Sam on 2009-06-10
Please post the output of **sudo fdisk -l**...

---

### Post by Geffers on 2009-06-13
> **Entropy_Sam said:**
> Please post the output of **sudo fdisk -l**...

Thanks for interest but resolved it by using the excellent tips on the following link;

[http://members.iinet.net.au/~herman546/p15.html#root](http://members.iinet.net.au/~herman546/p15.html#root)

Geffers

---

