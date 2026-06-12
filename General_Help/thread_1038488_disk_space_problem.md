---
title: "disk space problem"
date: 2009-01-12
forum: General Help
---

### Post by mabtifro2 on 2009-01-12
i'm quite certain that i had at least 1 gb free on my 3.7 gb filesystem, and all of a sudden now, it's 98% full and the system is running much slower than it was before.

by the way i have a 20 gb eeepc 900 (the 4 gb ssd runs the filesystem while my home directory is on the 16 gb ssd)

i ran sudo apt-get clean which only cleared about 50 mb.

i also ran the disk usage analyzer and the only thing that to me seems strange is the filesystem.squashfs file which is 673.9 mb. what is this file and why is it so large? the directory is /media/R\040R/casper/filesystem.squashfs

can someone please explain what that file does?

---

### Post by mabtifro2 on 2009-01-12
ahhh yes!!! someone pointed out to me that there is not supposed to be any files in media directory unless i have an sd card plugged in and i just realized why that huge r/r folder is there in the media directory. i erred on the first try when i was making a live ubuntu on my sd card using unetbootin and it copied all the system files into that folder. this is great news for me! but the bad news is... now i cant delete it, permission denied!!!!!!

how do i get around that?

---

### Post by drs305 on 2009-01-12
You can open nautilus or another file browser with administrative powers. **You will be able to delete any file system on your computer, so be very careful and be sure you know what you are deleting!**
```

gksudo nautilus
*or more specifically if they are in /media*
gksudo nautilus /media

```

After you have deleted the files, and you are confident you have deleted the correct ones, you will want to delete your root trash files as well. You can't delete them as a normal user. They will be located in either /root/.local/share/Trash/files or in the partition you deleted them in. You can prevent them from going into the trash bin by deleting using SHIFT-DEL, but once you have used this method to delete something there is no turning back.

---

### Post by mabtifro2 on 2009-01-12
free space = 1.1 Gib

PERFECT!!!!!!!!!!!!!!!!!!!!!!!!!!!!

THANK YOU SOOOOOOOO MUCH

---

