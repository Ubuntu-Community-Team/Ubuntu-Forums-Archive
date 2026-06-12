---
title: "mounting fs"
date: 2009-05-13
forum: Desktop Environments
---

### Post by vijaysarathy on 2009-05-13
hi all, 
i m new to linux..
i followed the instructions and succeeded in mounting two fat32 drives in ubuntu...
each time i needed to access them, i go to /mnt and access them...
how to get a shortcut to those mounted drives in the desktop..
this ques may be silly but pls help ..:)

---

### Post by logos34 on 2009-05-13
AFAIK, only if you mount them in /media will they show up on the desktop

---

### Post by aksheyjawa on 2009-05-13
You can definitely create a shortcut on your desktop. Shortcuts are called "links" in linux. You can try doing a drag and drop(of the folder where you are mounting the partition) from mnt folder to the desktop. If you want to do at command line-
```
ln -s /mnt/<folder name> /home/<username>/Desktop/
```

---

### Post by logos34 on 2009-05-13
are these usb flash drives?  Will they not [automount]("https://help.ubuntu.com/community/Mount/USB#Automounting")?

yeah, either use symlinks or change to /media directory mount (the default)

---

