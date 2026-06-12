---
title: "fstab error, How to fix?"
date: 2005-12-20
forum: General Help
---

### Post by Dislimit on 2005-12-20
fstab error, How to fix?

I added an option "iocharset=UTF8" (should be utf8, I think) to the root file system. Then the system can't be loaded corrently. If enter the recovery mode, the whole partition is set read-only. Is there any better way than reinstall the OS?

---

### Post by aysiu on 2005-12-20
Do you have a live CD?

---

### Post by Dislimit on 2005-12-20
Yes, I have an install CD.

---

### Post by Sutekh on 2005-12-20
aysiu means a "Live CD", different to your install CD.  

It will allow you to install an OS in your RAM, not affecting your hard discs, and then allow you to remove that line from your fstab.

He would suggest the Knoppix Live CD, but if you have an Ubuntu one that will do too.

I think you can boot into a console somewhere at the GRUB bootloader, but I'm not 100%

---

### Post by jliedeka on 2005-12-21
I haven't tried this with Ubuntu, but with most distros, you can boot from the install media and type "linux rescue" from the boot prompt.  That should boot you into a root shell where you will be able to edit your fstab.

---

### Post by az on 2005-12-21
Yes, there is a rescue mode on the breezy installer cd.  That is all you need.


Chroot into your ubuntu partition and edit fstab

nano fstab

You can even boot the installer, and when it asks about your keybaord, skip to CTRL-ALT-F2 and 
mkdir /mnt
mount /dev/hda3 /mnt
chroot /mnt
nano /etc/fstab

---

