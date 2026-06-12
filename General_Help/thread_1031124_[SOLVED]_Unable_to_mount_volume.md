---
title: "[SOLVED] Unable to mount volume"
date: 2009-01-05
forum: General Help
---

### Post by dE_logics on 2009-01-05
This has to be completely my fault.

I edited a volumes properties and made the mount point to /home...I unmounted it, then its not getting mounted!:confused:

I was using that partition for personal files and so I though mount it to /home would be a good idea.

---

### Post by Tim Sharitt on 2009-01-05
If you mount the volume as /home your home folder will no be usable (including all of your user configuration files) which is probably why it will not mount. You should mount your volumes to empty folders to avoid an problems.

---

### Post by dE_logics on 2009-01-05
I can't do that any more, since the volume cant be mounted, and so I cant view the tab in the properties dialogue from where you can change it.

---

### Post by Tim Sharitt on 2009-01-05
Sorry, I didn't realize how you were specifying the mount point. You may want to add an entry in fstab for the drive. The link below gives a very good inroduction to using mount and fstab. If you read over it and still have questions, I'll answer them the best I can.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by dE_logics on 2009-01-05
Thanks man!...done!:D

---

### Post by mattio26 on 2009-01-31
hi i'm having the same problem with a 16gb sdhc class 4 from play.com, i have read the link you have supplied but still am unable to get it to mount im a bit of a novice so please bear with me, the card shows up next to the files system but doesnt have the proper icon picture?

not sure if this is relevant but i keep getting the following line in terminal - dmesg

"VFS: Can't find ext3 filesystem on dev mmcblk0p1" 

is there any way u could tell me the correct line to write into the fstab?? 

thnx :)

---

### Post by diegodiaz on 2009-02-07
i have an other problem :( i can't mount any of my ntfs discs, i could mount them before but i upgraded my ubuntu and now i can't

---

