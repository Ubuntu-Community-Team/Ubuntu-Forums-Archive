---
title: "Easy Backup"
date: 2009-04-07
forum: General Help
---

### Post by mattlitke on 2009-04-07
I use SuperDuper! on my Mac to make bootable backups and I wanted to know if there is any application like that on linux.  I want to be able to make bootable copies on an external usb drive.  Im using an Eee PC 1000HE with Ubuntu 8.10

---

### Post by Eredeath on 2009-04-07
You can copy your entire OS to the USB drive by running 

sudo cp * <path to your usb>
(without the <>) from the root dir /

You might be able to use gparted and make the partition of the usb that you copied the os to bootable.

Disclaimer: I haven't done this, and cannot verify if it will work as i think it might. I hope this works/helps.

---

