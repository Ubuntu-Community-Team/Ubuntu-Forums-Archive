---
title: "Extract Xbox iso?"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Epeli on 2006-03-16
Is there any way to extract a Xbox iso dvd-image in Ubuntu since it is not possible to mount it with normal iso mounting methods?


Error:
```

$ sudo mount -t iso9660 -o loop xbox_dvd_image.iso  mount_dir/
mount: Not a directory

```


EDIT: Topic changed.

And how about creating one?
Or how can I burn those extracted files to a DVD+R that it would work in my Xbox?

---

### Post by Stealth on 2006-03-16
You may want to switch iso9660 to **udf** and try that?

---

### Post by slazh on 2006-03-16
Or you could try gXiso: [http://gxiso.berlios.de/](http://gxiso.berlios.de/)

Extract to dir, or send it directly to your xbox :)

---

### Post by Epeli on 2006-03-16
[QUOTE=Stealth]You may want to switch iso9660 to **udf** and try that?[/QUOTE]
Nope, doesn't work.
```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
I'll try the gxiso..

---

### Post by Epeli on 2006-03-16
Great!! gXiso seems to work!

But its ftp won't work...
"**Cannot create folder on Xbox:**
/e/games"


Btw: Is there any KDE version?

---

### Post by slazh on 2006-03-16
[QUOTE=Epeli]Great!! gXiso seems to work!

But its ftp won't work...
"**Cannot create folder on Xbox:**
/e/games"
[/QUOTE]
You'll have to make that dir yourself. Can be done with any FTP client,
if you have FTP enabled on your xbox that is :)

> Btw: Is there any KDE version?
Nope, this is the only version.
There might be similair programs though.

---

### Post by Epeli on 2006-03-20
And how about creating one?
Or how can I burn those extracted files to a DVD+R that it would work in my Xbox?

---

### Post by danrom on 2006-03-20
Wine Qwix from Team Avalaunch or if that gxiso app can grab from ftp, ftp into your xbox.

usr: xbox
passwd: xbox
server: 192.168.0.100

for folder just put /D/ or D/ after you inserted a game and make sure the app autopatches the iso or the backup will not work as well as the strait files to hdd.

---

### Post by sinaen on 2008-02-06
and how about a program that does the same in console please!

---

### Post by rattking on 2008-02-06
from the console
Extract-xiso
[http://sourceforge.net/project/showfiles.php?group_id=108585](http://sourceforge.net/project/showfiles.php?group_id=108585)

---

### Post by sinaen on 2008-02-07
Domo!

---

### Post by ThomasNovin on 2008-06-12
Or [http://xbgm.sourceforge.net/](http://xbgm.sourceforge.net/) which both has text-mode and GUI.

Edit: Can also add that Ubuntu packages are available.

---

