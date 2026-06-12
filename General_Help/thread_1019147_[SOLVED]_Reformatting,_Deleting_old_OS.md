---
title: "[SOLVED] Reformatting, Deleting old OS"
date: 2008-12-22
forum: General Help
---

### Post by biggiemokey on 2008-12-22
I reformatted my computer once (I use XP) and since then when I turn on my computer it gives me the option of booting to Microsoft Windows XP or Microsoft Windows XP - the second one doesn't work, though.  I am assuming that is the old OS that wasn't deleted properly - is there a way to get rid of this?  I am going to reformat soon to dual boot XP/Ubuntu and I don't want to see two old copies of Windows XP on there.  Thanks in advance for any help.

---

### Post by jimmy the saint on 2008-12-22
Wipe the drive (backup if neccessary first).  Make two partitions.  Install windows to one, THEN install Ubunut to the other.  It should work just fine.

If you need a good guide, just search for "dual boot windows ubuntu" and you will find dozens of great tutorials.

---

### Post by Chew N Tobacca on 2008-12-22
I have been through that process numerous times. When you re-install windows, make sure you DELETE the partition (rather than just installing) and re-partition from free space. You can then set your ntfs drives for windows and leave yourself some free space to install ubuntu. Upon starting the ubuntu install, you can create its own partition in the free space.

---

### Post by biggiemokey on 2008-12-22
Thanks, but would it be worth it to completely wipe the hard drive and start over, and just use a Live CD with GParted to set everything up?  I was going to use Secure Erase to wipe my drive.  Does anyone know any good free Disk Imaging programs for Windows XP?

---

### Post by sedawk on 2008-12-22
Have a look at boot.ini. I think there are two lines for booting XP
but you only need one of them.
(There is a way to see and edit that data using XP's GUI but I have no XP
 up and running to check where it is. You might have a look at the
 knowledge base articles from Microsoft to find out).

Hack boot.ini at your own risk!

---

