---
title: "customizing mount points"
date: 2008-05-19
forum: Desktop Environments
---

### Post by gangalee on 2008-05-19
I don't quite get the options in the Nautilus "Properties" Window/ Volume & Disk tabs. I want to change /media/disk to something else, how do I do it?

---

### Post by Inxsible on 2008-05-19
Use pmount to mount the memory card. ```
sudo aptitude install pmount
``` If you dont have it installed already. I think it is installed by default, but I could be wrong.

once installed```
pmount /dev/Xd*? MOUNT_POINT
```where X = s or h. s for sata and h for ide drives.
* = a,b,c,d....... i.e drive number
? = 1,2,3,4....... i.e. partition number

MOUNT_POINT is any name you like. Pick a name without spaces because its much easier that way. Make sure you use a name which is not already a mount point under /media. The pmount command will create a folder under /media for you.

---

### Post by pietjanjaap on 2008-05-19
install this
Storage Device Manager
start like this gksudo pysdm
Now you can mount to maps etc

---

### Post by gangalee on 2008-05-21
I guess I should've said, "see the attachment".
Nautilus is mounting it fine, and although pmount is nice, I'd like to know how to operate the existing options in the Nautilus properties.

---

### Post by geoganoe on 2008-06-03
You can just put the name of the folder under /media that you want it to go to into the "Mount Point:" selection.  You don't need to type the "/media/" part of the pathname (in fact if you do type the "/media/" part it is an error, and you will need to use the configuration editor to change it).

                         George

---

