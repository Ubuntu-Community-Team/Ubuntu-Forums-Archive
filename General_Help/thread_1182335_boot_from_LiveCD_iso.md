---
title: "boot from LiveCD iso?"
date: 2009-06-08
forum: General Help
---

### Post by scradock on 2009-06-08
I am having continued problems with my CD reader/writer. I can download an .iso file for the LiveCD, but cannot be sure that it will be written to CD correctly. Even if the CD appears to contain the correct folders and files I am not able to successfully boot from it. The CD reader works for music CDs, but not (reliably) as a boot device, even for older version LiveCDs that I know are correctly written.

I am wondering if there is a way to circumvent this blockage and set up the .iso, perhaps after "opening" it with Archive Manager, as a pseudo-LiveCD environment, to try out new versions and eventually install to another partition. Can I chroot into it, for instance? If so, how, exactly?

My BIOS does not allow booting from USB, so making a USB stick install will not work; neither will buying a USB external CD reader. It seems at the moment that my only option is to buy a new internal (laptop) CD RW drive.

Or does anyone have another idea?

---

### Post by 123456789123456789123456 on 2009-06-08
I'm not sure about the iso question, though booting from an ISO unless you use a virtual machine with emulation software is not possible as far as I understand.
go to [www.newegg.com](www.newegg.com) for prices on cheep laptop drives.
they are usually very cheep with drives, and other parts.  I use them alot, even in the computers I build for people, and have never has a problem with the drives.

---

### Post by MyR on 2009-06-08
To boot live media you need either a reliable optical (CD) drive or a motherboard that supports booting from USB.  AFAIK there's no way for BIOS to emulate another boot device.

peace

---

### Post by scradock on 2009-06-09
Thanks - I was afraid of that. If it was already "installed" there might be a chance, but I doubt I could chroot into an initramfs to any good effect.....

Oh well, that's life. Just because the OS is free it doesn't mean the hardware has to be too....

---

