---
title: "How can I downgrade X.org 1.13 to X.org 1.12 on Ubuntu 12.10?"
date: 2013-02-11
forum: Desktop Environments
---

### Post by GnuKian on 2013-02-11
I need to downgrade the X.org to install ATI driver. The amd has announced automated installer and Display Drivers in [version 13.1]("http://support.amd.com/us/kbarticles/Pages/AMDCatalyst131ProprietaryLinuxGraphicsDriverReleaseNotes.aspx") for 4xxx/3xxx/2xxx cards just work under Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4

So, How should I downgrade x.org and ban it to future upgrade? what's the instruction?


kind regards.

---

### Post by GnuKian on 2013-02-12
bump,
downgrading kernel will downgrade the x.org?

---

### Post by ali abry on 2013-02-12
no.
xorg is a separate package .

---

### Post by 3Miro on 2013-02-12
Every now and then AMD will drop the support for their proprietary drivers for newer versions of Xorg and kernel. Downgrading something like that is complicated, your best bet is to either use the default driver or use an older version of Ubuntu.

---

### Post by GnuKian on 2013-03-04
> **3Miro said:**
> Every now and then AMD will drop the support for their proprietary drivers for newer versions of Xorg and kernel. Amd announced will never release any driver for old cards as in 4xxx series!


> Downgrading something like that is complicated, your best bet is to either use the default driver 
the system is for my little brother and it's needed to install propriety driver on ubuntu 12.10 to playe games!


> or use an older version of Ubuntu.
the current version is ubuntu 12.10 with many packages and a heavy config for the kid; installing a fresh one is wasting time!
:(

---

