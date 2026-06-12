---
title: "How to edit your boot-loader without reinstall?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by jms1989 on 2006-09-15
I recently modified my HDD setup, hoping for a boost in performance, and I need to find a way to permenly modify the boot loader. The way I want it is for when I turn on the pc, it goes through it's traditional boot screens and then to the boot menu listing windows and linux. After the menu I want it to go directly to linux as it did before the modifacation.

Currently I have to edit the boot menu, but it's only temporary, just to load Ubuntu. On my next bootup or restart I'll try to get a picture of the menu.

I want to know if there is a command, file, or program that will let me edit it. The previous setup had my 250GB HDD as master and my 40GB HDD as slave, all I did was changed the jumpers. The HDDs are connected the same, and in the same order, 250GB on top of the 40GB with the end of the 40-pin connected to the 250Gb and the proceeding plug connecting to the 40GB.

I'll get some pics if you need them.

Thanks,
jms1989.

---

### Post by Odinist on 2006-09-15
Make the changes you want in the /etc/fstab file. =)

---

### Post by jms1989 on 2006-09-15
> **DruidicWisdom said:**
> Make the changes you want in the /etc/fstab file. =)

Everything in that file are correct,

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1    /media/HDD1 ntfs  nls=utf8,umask=0222 0    0
/dev/hdb2    /media/HDD2  ext2  suid,dev,exec  0  0


hda is the 40GB hdb is the 250GB

---

### Post by Odinist on 2006-09-15
Crap, sorry, I'm at work, it's Friday, my head is not working right!!!

Totally not the file I meant to tell you to edit.

Find the grub.conf file. That's the one you wanna play with.

---

### Post by MetalMusicAddict on 2006-09-15
You will also have to edit: **/boot/grub/menu.lst**.

---

### Post by Odinist on 2006-09-15
^^^ What he said.


I'm totally done giving advice for the day.

---

### Post by jms1989 on 2006-09-15
Thanks for the info. I've modified my menu.lst file to work correctly.

---

