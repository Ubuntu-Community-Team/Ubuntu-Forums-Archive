---
title: "[SOLVED] GNOME Trash, unable to delete file"
date: 2008-08-08
forum: Desktop Environments
---

### Post by Okar on 2008-08-08
Hi,
I got a directory in my Trash for which I have no permissions to delete it. I don't know how this happend....really odd

the folder ~/.local/share/Trash/files is empty though.
does anyone know how I could delete this file? are there other folders that should contain the trash?

ty

---

### Post by tuxxy on 2008-08-08
Open terminal and type

```
gksudo nautilus /home/[your username]/.local/share/Trash/files
```

Now delete the files you want

---

### Post by lordadi on 2008-08-08
Hi,


I had a similar problem :[http://ubuntuforums.org/showthread.php?t=870245]("http://ubuntuforums.org/showthread.php?t=870245")


Cheers,


Lordadi.

---

### Post by Okar on 2008-08-08
I figured out the problem, it was a file that I deleted on my external harddisk.
the folder was in a folder called ./Trash-1000 on /media/disk.

---

### Post by tuxxy on 2008-08-08
Excellen t, now you can mark your thread as solved :)

---

