---
title: "Want to avoid Grub in MBR"
date: 2009-04-27
forum: Desktop Environments
---

### Post by alexham on 2009-04-27
Hi, Guys,

I would like to experiment with Ubuntu, but until I am sure that everything works, I would like to unplug my normal HD and install on a spare HD.  Is there a way to avoid the Grub being written to MBR?

Another question, if I may.  Is it possible to install Ubuntu onto a DVD and run it from there?

Many thanks,

Alex

---

### Post by calvinps on 2009-04-27
> **alexham said:**
> Hi, Guys,

I would like to experiment with Ubuntu, but until I am sure that everything works, I would like to unplug my normal HD and install on a spare HD.  Is there a way to avoid the Grub being written to MBR?

Another question, if I may.  **Is it possible to install Ubuntu onto a DVD and run it from there?**

Many thanks,

Alex

Ahem! You can run Ubuntu from its CD. You may have not heard of this, but it's called a **Live CD**. One advantage of using it is that it doesn't change your computer at all! One disadvantage of using it from the CD though is that documents and settings, etc., cannot be saved on-the-fly, but a solution would be that should you need to save your work, you could use a USB flash drive or something to store your documents. ;)

---

### Post by mtbsoft on 2009-04-28
You should be able install to an external (USB) hard drive and set your bios to boot from USB before it boots from the internal hard drive.  If you want Ubuntu, plug in the drive and (re)boot;  if you want Windows, unplug and (re)boot.

It might make your boot cycle a few seconds slower as it scans for bootable USB devices but it will allow you to do a full install which will preserve any customisations you make.

---

### Post by tkoco on 2009-04-29
Provided that the BIOS on the motherboard supports booting from USB, you could either 1) install Ubuntu to the external HD as already suggested, or 2) Create a bootable USB stick with a persistant storage.
To find out more info on a bootable USB stick, search Google for 'ubuntu bootable USB stick'. Plenty of good tutorials out there.

If the motherboard does not support booting from USB, you can still use the Live CD as already suggested.

> **alexham said:**
> Hi, Guys,

I would like to experiment with Ubuntu, but until I am sure that everything works, I would like to unplug my normal HD and install on a spare HD.  Is there a way to avoid the Grub being written to MBR?

Another question, if I may.  Is it possible to install Ubuntu onto a DVD and run it from there?

Many thanks,

Alex

---

