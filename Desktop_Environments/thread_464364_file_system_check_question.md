---
title: "file system check question"
date: 2007-06-04
forum: Desktop Environments
---

### Post by steve3226 on 2007-06-04
After every 30th boot up, Ubuntu goes through a long file system check. How can I modify the check  to every 100th boot up?

Steve

---

### Post by loserboy on 2007-06-04
as far as I can tell that info is stored in /etc/fstab

I found the info in this thread, but it doesnt really pertain to your problem
[http://ubuntuforums.org/showthread.php?t=426344&highlight=checkfs](http://ubuntuforums.org/showthread.php?t=426344&highlight=checkfs)

---

### Post by Rui Pais on 2007-06-04
changing /etc/fstab have only a limited set of possibilities:
never do checks, check root/other filesystems. 

If you want to set a different time period (better then set to never check), you need to boot from a liveCD and do on a terminal:
```
sudo tune2fs -c N -i T /dev/xxx
```

where N is the number of boots before check (i usually set this to 0, you can set to 100) 
T is a time, i usually set this to 6m, (means 6 month, you can set to 0 if you set N as 100)
and, of course, xxx is your partition number sda1, sdb2, hda3, whatever.

---

### Post by loserboy on 2007-06-04
well I was only way off

---

