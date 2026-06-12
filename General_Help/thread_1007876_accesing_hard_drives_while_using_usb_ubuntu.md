---
title: "accesing hard drives while using usb ubuntu"
date: 2008-12-10
forum: General Help
---

### Post by BufordPants on 2008-12-10
Hello, I was wondering how I can access files on the main hard drive/s (e.g. drive c) if I boot from a USBD with Ubuntu on it?

---

### Post by dragos_iliescu_2005 on 2008-12-10
you probably see something like sda, sdb...

---

### Post by BufordPants on 2008-12-11
Maybe I need to be more clear.  I want to access files on my hard drive, that for some reason, I am unable to do when I boot Ubuntu 8.10 from my USBD.  I already know how to boot from the USBD, and have been successful at booting a persistent Ubuntu from the USBD.  I want to know how to access files on my hard drive, e.g. mp3 files that are not on the usbd; they happen to be on drive C.  I would guess that I can  do this by becoming superuser -- I am not really sure. I am open to suggestions.

---

### Post by dragos_iliescu_2005 on 2008-12-11
Drive C named so by WIndows, usually named as sda or sdb or whatever letter here by Linux. You just need to mount that hdd. Let make same search for your partition on the system. Boot from USB and,
open terminal, type: "sudo fdisk -l" and paste here the output.

---

