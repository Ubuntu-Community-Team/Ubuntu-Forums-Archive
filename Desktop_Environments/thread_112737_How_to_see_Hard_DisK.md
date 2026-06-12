---
title: "How to see Hard DisK?"
date: 2006-01-05
forum: Desktop Environments
---

### Post by GoDaddy on 2006-01-05
Hi, i'm totally new to linux. I just installed today ubuntu :D

I have 3 HD, 1 for Windows, 1 for Linux and 1 for Data. 

The one for data, i'm unable to see it in Ubuntu ... can someone tutor me how to do so i can get to my data files .. like mp3 ... 

Thanks,

---

### Post by Omnios on 2006-01-05
read this its about mounting windows drives.

[http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

 I have a similar set up with a XP drive a vfat32 drive for data (my documents) and a linux drive I use this in fstab to mount my fat drive with permisions and it shows up in menu / Places / Computer
```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
```

 Note Linux can read ntfs but can not write to it. Linux can both read and write to a vfat32 drive.

This page explaines how fstab works
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

