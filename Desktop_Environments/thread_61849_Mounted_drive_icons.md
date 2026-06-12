---
title: "Mounted drive icons"
date: 2005-09-02
forum: Desktop Environments
---

### Post by cbudden on 2005-09-02
Hellloooooo
The last session i used ubuntu (before a log off) my two mounted windows partitions, mydocs and windows appeared as a drive icon on my desktop.  After logging off and on, they have gone!  All i am left with is the original folder link.  The icons first came up during that session aswell.  
How can i make this permanant?


Thanks
Chris

---

### Post by KingBahamut on 2005-09-02
Mounted, as in they are drives on your system. 

If so, youll need to edit fstab with something like this. 

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

see [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for further detail.

---

### Post by cbudden on 2005-09-02
[QUOTE=KingBahamut]Mounted, as in they are drives on your system. 

If so, youll need to edit fstab with something like this. 

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

see [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for further detail.[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/mydocs  ntfs    nls=utf8,umask=0222 0       0
/dev/sda1  	/media/usb  vfat  defaults,rw,noauto,users,sync  0 0


How can I get the mounted drive to be a icon on my desktop?

---

### Post by cbudden on 2005-09-02
[http://www.ubuntuforums.org/showpost.php?p=280726&postcount=3](http://www.ubuntuforums.org/showpost.php?p=280726&postcount=3)

When I do this, it works but how can I get it to run automatically?

---

### Post by Aero-Z on 2005-09-02
I updated my Ububtu Hoary yesterday and after that I too had Windows like a drive in My Computer and on my Desktop. After logging out and on again, they were gone. How to make mounted Windows partition like filesystem?

---

### Post by cbudden on 2005-09-02
[QUOTE=Aero-Z]I updated my Ububtu Hoary yesterday and after that I too had Windows like a drive in My Computer and on my Desktop. After logging out and on again, they were gone. How to make mounted Windows partition like filesystem?[/QUOTE]
 I read this from this thread [http://www.ubuntuforums.org/showpost.php?p=117054&postcount=24](http://www.ubuntuforums.org/showpost.php?p=117054&postcount=24)
and did what it said.  which worked!!!!!!!  YAY

---

