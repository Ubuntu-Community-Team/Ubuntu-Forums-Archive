---
title: "Does this make any  sense?"
date: 2009-05-07
forum: General Help
---

### Post by Garofoli on 2009-05-07
Hey [ubuntu],
Since I got my computer, I've always had space issues with my hard drive. At this point, I was adding up all my files and figured that the number didn't add up.I then came across this. Can anyone explain this image? Thanks.:D

[IMG]http://i40.tinypic.com/9uvy2q.png[/IMG]

---

### Post by freonchill on 2009-05-07
well the image looks like you have compiz fire on (the red marks)

but the free vs space available vs full is understandable if you know one thing...

unix/linux keeps 5% free disk space for root to login (which would create a log and if that space is not available, you get error messages)

[http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips#Reclaim_Reserved_Filesystem_Space](http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips#Reclaim_Reserved_Filesystem_Space)

i had this problem a couple of months ago
changed it to 1% (from default of 5%) and was able to use all but 600mb of my drive.

---

### Post by drs305 on 2009-05-07
If you wonder why the disk is almost full, take a look at the link in my signature line about finding lost disk space. You could have unremoved trash, made a backup to your system partition instead of a backup drive, have large log files, etc. Additionally, different apps report available space differently. The linked guide explains most of it.

If your concern was more in line with what freonchill wrote, the tune2fs command will change the settings if that is what you want.

---

### Post by Garofoli on 2009-05-07
Thank you very much, just what I needed. And nice eye seeing the fire, I didn't even realize it.

EDIT: Actually the command isn't working. Nothing happens when I put the "# tune2fs -m 1 /dev/sdXY" command in. Any ideas?

---

### Post by drs305 on 2009-05-07
> **Garofoli said:**
> Thank you very much, just what I needed. And nice eye seeing the fire, I didn't even realize it.

EDIT: Actually the command isn't working. Nothing happens when I put the "# tune2fs -m 1 /dev/sdXY" command in. Any ideas?

Did you use *sudo*, substitute your actual device name and remove the # symbol?
Here is an example for /dev/sdb1:
> sudo tune2fs -m 1 /dev/sdb1

---

### Post by Garofoli on 2009-05-07
When I type in the updated code, i get...

tune2fs 1.41.3 (12-Oct-2008)
tune2fs: No such file or directory while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

---

### Post by drs305 on 2009-05-07
Your device is probably *not* sdb1 or you did not include "sudo" at the start of the command. You can run this command to find out what devices you have. Most likely you have *sda1*.
```
sudo fdisk -l
```

---

### Post by Garofoli on 2009-05-07
Sweet, thanks a lot guys!

---

