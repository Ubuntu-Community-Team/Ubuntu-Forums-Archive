---
title: "Ubuntu and SATA cdrom"
date: 2009-08-09
forum: Development CD/DVD Image Testing
---

### Post by larka06 on 2009-08-09
I am using a SATA DVD/CD writer that will not work with Ubuntu 9.04 Distro. I have not tried the other versions so the problem may only be with the 9.04.  At any rate this problem has sent me back to fedora for now.  I would like to know it anyone knows about this and, is it going to be corrected?
Thanks all

---

### Post by bertmanphx on 2009-09-17
larka06,
I have one machine that is very picky that way too.  It seems to be the SATA / Chipset interaction, not the drive itself.  I've worked around it by using the text install, and alternate CD.  

Have you tried booting using a USB drive?  That could get you a minimal system.

bertman

---

### Post by jpkotta on 2009-09-17
Post the output of lspci.

You could try changing the AHCI setting in the BIOS, if there is one.  If you have Windows installed, enabling AHCI may cause it not to boot.

---

### Post by rajeev1204 on 2009-09-25
> **larka06 said:**
> I am using a SATA DVD/CD writer that will not work with Ubuntu 9.04 Distro. I have not tried the other versions so the problem may only be with the 9.04.  At any rate this problem has sent me back to fedora for now.  I would like to know it anyone knows about this and, is it going to be corrected?
Thanks all

BY any chance,are you using an amd 690g chipset?

---

### Post by foremannz on 2009-09-25
I use a SATA SSD and SATA DVD-RW, and I've had no problems installing it.

---

