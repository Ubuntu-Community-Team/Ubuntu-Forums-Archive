---
title: "How can i fix Vista MBR from Ubuntu? PLEASE READ"
date: 2009-05-12
forum: General Help
---

### Post by david4141 on 2009-05-12
Hi, ok heres the problem

I've messed up my Vista boot and now it wont start and i cant even access safe mode or anything and i dont have the Vista CD to repair it. So luckily i have a Ubuntu CD which im running from the disc right now and i need a way to fix my Windows Vista boot from Ubuntu so i can get back on it again. Is there any software like Easy BCD Edit for Ubuntu?

please help :(

---

### Post by kellemes on 2009-05-12
[SuperGrubDisk]("http://www.supergrubdisk.org/") may be able to fix Vista's bootloader.
Browse [the wiki]("http://www.supergrubdisk.org/wiki/Main_Page") for more info..

---

### Post by FIONEX on 2009-05-12
you just need a start up floppy disk or a boot cd of some sort.  There's UBCD and other boot CDs that you can download and burn for free.  Anyways, you boot with the cd, and type this:  fdisk /mbr.  That should work in theory.

---

