---
title: "Changes to XORG.CONF do not save"
date: 2009-01-12
forum: General Help
---

### Post by iincognito_73 on 2009-01-12
Hi, I am new to Linux.  I have setup Ubuntu 8.10 on a flash drive.  Any changes made are persistent on the drive EXCEPT any changes I make to the xorg.conf file.  If I make a change to the xorg.conf and restart X, the changes are there.  But if I reboot the flash drive, the changes are not there.  I  been reading the posts and seem confused on whether xorg.conf can be saved.  I really need the changes to be persistent because it allows me to use my stylus pen on my tablet PC.  Thanks for any help/suggeation!

---

### Post by dcstar on 2009-01-13
> **iincognito_73 said:**
> Hi, I am new to Linux.  I have setup Ubuntu 8.10 on a flash drive.  Any changes made are persistent on the drive EXCEPT any changes I make to the xorg.conf file.  If I make a change to the xorg.conf and restart X, the changes are there.  But if I reboot the flash drive, the changes are not there.  I  been reading the posts and seem confused on whether xorg.conf can be saved.  I really need the changes to be persistent because it allows me to use my stylus pen on my tablet PC.  Thanks for any help/suggeation!

The Live CD based USB install will probably always do an autodetect as it is meant to boot up off any hardware to do an install - and this means the xorg file is created on each boot.

You can try making the xorg.conf file read only, or you may have to do a standard install onto the USB drive to be able to make permanent changes to the xorg file - or install one of the eee-pc Ubuntu distros that are optimised to run off solid-state drives (like your USB stick).

---

