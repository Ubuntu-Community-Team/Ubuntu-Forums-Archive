---
title: "Ubuntu/vista mess, please help"
date: 2009-01-22
forum: General Help
---

### Post by kuriozux on 2009-01-22
Someone please help me.

I was able to install Ubuntu on my Vista machine and got it to work beautifully. The I decided to change the size of the partition for Ubuntu, but somehow I deleted the partition for Windows. I then decided to delete all partitions, re-install windows, and re-install Ubuntu with Wubi.

The problem now is that I cannot boot from my windows cd. It keeps going to Ubuntu Grub without any sign of booting from widows cd. What can I do to install both back on my machine?

Thanks to whoever helps.

---

### Post by lloyd_b on 2009-01-22
> **kuriozux said:**
> Someone please help me.

I was able to install Ubuntu on my Vista machine and got it to work beautifully. The I decided to change the size of the partition for Ubuntu, but somehow I deleted the partition for Windows. I then decided to delete all partitions, re-install windows, and re-install Ubuntu with Wubi.

The problem now is that I cannot boot from my windows cd. It keeps going to Ubuntu Grub without any sign of booting from widows cd. What can I do to install both back on my machine?

Thanks to whoever helps.
You probably need to get the into the machine's BIOS setup, and change the "boot order" option - it's probably set to try the hard drive before the CD drive.

Hopefully, when you start up the machine, it gives you a "press F2 for setup" or similar option to tell you how to get into the BIOS.  Otherwise, you'll have to dig through the manual for the machine or google for the instructions.

---

### Post by kuriozux on 2009-01-22
> **lloyd_b said:**
> You probably need to get the into the machine's BIOS setup, and change the "boot order" option - it's probably set to try the hard drive before the CD drive.

Hopefully, when you start up the machine, it gives you a "press F2 for setup" or similar option to tell you how to get into the BIOS.  Otherwise, you'll have to dig through the manual for the machine or google for the instructions.

Hi,

I have the CDROM as first option in BIOS, but it starts the grub and no options from CD. Any other thoughts?

Thanks fot the response by the way.

---

### Post by caljohnsmith on 2009-01-23
Can you boot any other bootable CD in your CD drive? For instance, can you boot your Ubuntu Live CD?

---

