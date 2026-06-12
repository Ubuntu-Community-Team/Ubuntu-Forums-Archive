---
title: "Dang Small Linux USB"
date: 2008-11-18
forum: Desktop Environments
---

### Post by Stargazer989 on 2008-11-18
i've tried to use VirtualBox-ose to use DSL and install DSL via vbox but it didn't work because i can't seem to find a way to mount the usb drive so that DSL under vbox can see it. any ideas ? 3.4 for DSL version.

**EDIT: i think this is the wrong section that i posted in. could a mod move it for me ?
please and thank you.

---

### Post by kerry_s on 2008-11-18
with virtualbox just download the iso and use that to install.
[http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso](http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso)

---

### Post by Stargazer989 on 2008-11-18
no, i want to make my usb stick a 'LiveCD' because my mini laptop has no CD drive...

---

### Post by tgalati4 on 2008-11-19
I loaded DSL (3.0.1) by removing the hard drive from an old laptop and putting it in a desktop (using an IDE-to-notebook-drive adapter).  Boot the PC with DSL, use the tools to perform a harddisk install.  

If you just want a USB stick install then you can simply boot any desktop/laptop with a CD drive (preferably an older machine--2.4 kernel may not boot correctly on the latest hardware) and use the installation tool to format and load DSL to the USB drive.  You can manually partition the USB drive and dd the ISO image to the USB stick, but I've had problems with that method.  Sometimes you need FAT16 on the first partition for "Boot-from-USB" to work on some machines.

If you search the dsl forums, you will come up with other suggestions as well.

---

### Post by kerry_s on 2008-11-19
> **Stargazer989 said:**
> no, i want to make my usb stick a 'LiveCD' because my mini laptop has no CD drive...

my bag i miss under stood.
what your saying is you already have DSL running in virtual box and you want it to install to the usb.

i would suggest skipping virtual box altogether and follow the wiki:
[http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)

---

### Post by Yownanymous on 2008-11-19
You don't actually need Virtualbox. Virtualbox is like a totally different computer, but one you can't use physically.

---

