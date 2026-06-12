---
title: "New SCSI hard drive icon"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by BisonteNegro on 2008-02-19
Hi there,

I just added a new SCSI hard drive, I've mounted the disk in /mnt/data. The problem is that to get there "visually" I have to navigate through my filesystem. Is there any way I can show  my new hard drive in the computer screen and access its contents by double clicking on it? 

Thx in advance!

---

### Post by BillDozer on 2008-02-19
You can drag it to the desktop by holding the scroll button on your mouse.

---

### Post by jeffus_il on 2008-02-19
If you mount your drive's partitions using /etc/fstab they will always be part of the file system. You could simply keep bookmarks in Nautilus or use shortcuts on the desktop. If you do not mount them using the fstab file, they will be displayed as an icon on the desktop, if Nautilus is set up to show desktop icons.

---

### Post by BisonteNegro on 2008-02-19
Thx for the quick feedback!!

How can I mount them without the fstab? I only know that way....

Thx

---

### Post by hyperair on 2008-02-19
Mount it to /media/data instead of /mnt/data. Then it'll appear on your desktop.

---

### Post by BisonteNegro on 2008-02-19
I mounted in /media/data but is not showing up anywhere....

Here is my fstab:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98d0a276-c747-4344-9fca-157bde9ee172 /               ext3    defaults,errors=remount-ro 0       1
#/dev/sdb1
UUID=b730dd38-6b5f-4135-b362-c229a5b75980 /media/data       ext3    auto,defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d35929a8-0afa-4a39-af32-9c6000430488 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0[/B]

---

### Post by hyperair on 2008-02-19
Does it appear in Computer?

---

### Post by BisonteNegro on 2008-02-19
Nope, it doesn't :(

---

### Post by BisonteNegro on 2008-02-19
I forgot to reboot !! Now it works sweet! Thank you so much!!!

---

