---
title: "Prevent Mount Icons On Desktop"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Drunken Pirate on 2006-01-08
I would like to have my Windows NTFS mount points not listed on my Desktop. (I would like my floppy, cd, etc..)

---

### Post by art on 2006-01-09
As described here 

[http://ubuntuforums.org/showthread.php?t=114369](http://ubuntuforums.org/showthread.php?t=114369)

HTH

---

### Post by Drunken Pirate on 2006-01-09
That kinda works, but isn't quite what im looking for. I still want it in the Places list, as well as in the sidebar on nautilus.

---

### Post by art on 2006-01-09
If you bookmark it in Nautilus, you'll have it in Places

---

### Post by Drunken Pirate on 2006-01-09
Ok, howabout in "Computer"? You know the folder that lists Filesystem, Floppy, CDROM, etc...

---

### Post by soulestream on 2006-01-09
open a terminal and type

gconf-editor

go to 

apps
nautilus
desktop
uncheck  volumes_visible

as an example this will leave the a mounted cd visible in nautilius side bar and under places. 

However they will not be on desktop.

soule

---

### Post by Buffalo Soldier on 2006-01-09
[QUOTE=soulestream]open a terminal and type

gconf-editor

go to 

apps
nautilus
desktop
uncheck  volumes_visible

as an example this will leave the a mounted cd visible in nautilius side bar and under places. 

However they will not be on desktop.

soule[/QUOTE]
That would also hides his CD, floppy, thumbdrives and etc... which he wants to be visible on the desktop.
[QUOTE=Drunken Pirate]I would like to have my Windows NTFS mount points not listed on my Desktop. (**I would like my floppy, cd, etc..**)[/QUOTE]

---

### Post by Drunken Pirate on 2006-01-09
Thanks for trying guys. I have done extensive searching, and have come up with nothing. Seems like there isn't any way to do it.

---

### Post by art on 2006-01-09
Well, Computer lists stuff that's mounter on /media, hence you can't have it there and not on desltop... Having it in Bookmarks is exactly the same thing, in my opinion though:)

---

