---
title: "Can't boot after enabling nvidia drivers"
date: 2011-02-13
forum: Desktop Environments
---

### Post by wondr on 2011-02-13
Hey!

After upgrading to natty alpha I enabled the nvida graphics drivers. Now I can't boot and get stuck on a purple screen, without grub.
Can I with a live cd revert the drivers back to normal?

---

### Post by Krytarik on 2011-02-13
> **wondr said:**
> 
Can I with a live cd revert the drivers back to normal?
No, not without "chrooting" into your system from there, a bit complicated.

Did you already try booting into recovery mode?!

EDIT: Oh, without Grub, then press "Shift" to get the boot menu.

---

### Post by wondr on 2011-02-14
it doesn't response at all when stuck at that purple screen. shift did nothing.

---

### Post by Krytarik on 2011-02-14
> **wondr said:**
> it doesn't response at all when stuck at that purple screen. shift did nothing.
You have to press Shift right after your BIOS screen, or even before, just to be sure.;)

If you have Grub legacy instead of Grub2, press Esc.

---

### Post by shademere on 2011-05-04
Hello there,

I have a simliar problem. After installing the drivers I can get to GRUB, but neither the normal nor recovery boot options work. The normal option hangs at 

[FONT="Courier New"]mountall: disconnected from Plymouth[/FONT]

while in recovery mode the boot hangs and shows the message

[FONT="Courier New"]ata6: SATA link down (SStatus 0 SControl 300)[/FONT]

What could be the problem? How can boot from a recovery/installation disk? How does chroot work?

Thank you.

---

### Post by Krytarik on 2011-05-04
shademere, try setting "nomodeset" as a kernel boot option:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

