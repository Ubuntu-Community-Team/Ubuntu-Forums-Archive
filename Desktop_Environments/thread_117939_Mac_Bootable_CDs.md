---
title: "Mac Bootable CDs"
date: 2006-01-15
forum: Desktop Environments
---

### Post by doublesix on 2006-01-15
I have downloaded the ISO for the PowerPC version of Ubuntu Breezy. I can burn it successfully with GnomeBaker, but the resulting CD is not bootable. Are there any settings I need to change in order to be able to burn a Mac bootable CD under linux?

---

### Post by Sef on 2006-01-15
A couple questions for you:

1) did you do an md5sum check?

2) Is the Mac set to boot from the CD rom before the hard disk?

3) Is there another mac you could try it in to see if it works if you did the above?

---

### Post by aysiu on 2006-01-15
Generally with Macs you have to hold down the *C* key right after you boot it up in order to boot from CD-ROM.

---

### Post by doublesix on 2006-01-16
The mac can read it just fine, but it can't boot from it using the C key or any other boot key combo. I'm thinking the CD has to be burned as HFS in order to be mac-bootable. Is there any way to burn such a cd under linux?

---

### Post by aysiu on 2006-01-16
[QUOTE=doublesix]The mac can read it just fine, but it can't boot from it using the C key or any other boot key combo. I'm thinking the CD has to be burned as HFS in order to be mac-bootable. Is there any way to burn such a cd under linux?[/QUOTE] No, I burned a PowerPC Ubuntu ISO on my  x86 Linux PC and used it on my wife's Powerbook, and it worked fine.

You're definitely burning it as a disk image?

If you want to burn it from a Mac, just go to Applications > Utilities > Disk Utility > Burn > Image

---

