---
title: "Viewing Windows"
date: 2005-11-16
forum: Desktop Environments
---

### Post by bathini on 2005-11-16
Hello friends

I am trying to view my .pdf file which is in windows partition. When I click Places my partitions are mounted but when I click on the Hda2 icon (Windows partition)it talks about permission???I do not have sufficient permission to view. Please help and thanks

Bathini

---

### Post by yyagol on 2005-11-16
[QUOTE=bathini] When I click Places my partitions are mounted but when I click on the Hda2 icon (Windows partition)it talks about permission[/QUOTE]

post your fstab so we can have some detales

---

### Post by canadianwriterman on 2005-11-16
I'm not sure if you mean you can't see the files or can't open them.I believe you can also copy the PDF from your Windows drive, paste it into a folder in Ubuntu and change the permissions. In my setup, all the files in Windows are locked. Although I can still "read" them, they are read only.

---

### Post by yyagol on 2005-11-16
They Must Be a read only otherwise you will end up with
a no good windows os
must have umask=0222

---

### Post by bathini on 2005-11-19
What is fstab? I am not sure were to get this file?Thanks

bathini

---

### Post by taurus on 2005-11-19
It's called /etc/fstab where you mount all your partitions during boot.  If you want to view the content of it, do

more /etc/fstab

---

### Post by aysiu on 2005-11-19
Read this:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

If you need to know where to type the commands given, go to Applications > Accessories > Terminal.

---

### Post by bathini on 2005-11-23
Hello friends

This is my fstab

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Cheers

---

### Post by aysiu on 2005-11-23
[QUOTE=bathini]
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0[/QUOTE] This is your problem. *defaults* means you can read it only as root. Please refer to what I linked to above in order to fix this.

---

