---
title: "Language (hebrew) promlems in KDE"
date: 2007-01-23
forum: Desktop Environments
---

### Post by Caligula on 2007-01-23
Hey all.

I seem to have a problem with KDE. It just doesn't work well with the hebrew.
For example, i can't save files or folders with hebrew names, they just turn into question marks. Another thing is that i can't write hebrew in konsole, it also turns into question marks.

oh, and it's an install of Debian Etch, i just came here because it's the besdt forum I know (:

thanks,
Josh 8)

---

### Post by ComplexNumber on 2007-01-23
> **Caligula said:**
> Hey all.

I seem to have a problem with KDE. It just doesn't work well with the hebrew.
For example, i can't save files or folders with hebrew names, they just turn into question marks. Another thing is that i can't write hebrew in konsole, it also turns into question marks.

oh, and it's an install of Debian Etch, i just came here because it's the besdt forum I know (:

thanks,
Josh 8)
have you got both the fonts and the language packs installed?

---

### Post by Caligula on 2007-01-24
yes. hebrew does work. I can read and write hebrew, and I can even make all my apps (menus & stuff) to appear in hebrew. 
The only problem is saving files & folders in hebrew, or writing in hebrew in the konsole. If i want to save a file in hebrew, i give it the name, click enter, and after a few seconds the file name turns into a bunch of question marks. 

I think it may be a problem in the filesystem, is that possible? that maybe i can't write in hebrew on the filesystem? I don't know if i'm in the right direction, but this is my /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hdd        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
```

---

