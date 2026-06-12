---
title: "Disk mounting on KDE"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Movikun on 2005-08-16
Another question about KDE : 

It seems KDE by default uses hal or some other mechanism to auto-detect and mount hard drive partitions. This has 2 flaws for me : 

-I like to specify my own mountpoints, right now all the mounts are in /Volumes , /media however is a symlink to that directory

-This mechanism autodetects the partitions, but displays them as "<Somesize> G Media. I have 12 partitions, and it leaves me baffled to which one is which, not to mention it is ugly when shown on the desktop. 

Is there any way to make kde look ONLY to fstab for the mounted disks, so that when i select the options "show mounted volumes on desktop" it displays and manages partitions via fstab rules? (For example mounting/unmounting of those partition straight from the desktop, YES, my user has priviliges to do this :))

Thanks for any help

---

### Post by Martin Witte on 2005-08-16
I do not have an answer to all your questions, but the Konqueror issue showing only icons with sizes is a setting issue: go to View, View Mode in the menu, choose Tree View (some others work as well), then go to the View, Show Details menu - set Show URL on, now you have an URL column as last column, you can drag this forward

---

### Post by Movikun on 2005-08-16
It seems your post got cut-off... or is it not?

---

### Post by Martin Witte on 2005-08-17
No - I'm afraid that's all Im got on this....

---

