---
title: "cron ?"
date: 2006-03-16
forum: Desktop Environments
---

### Post by rfruth on 2006-03-16
Okay so every 30 boots a (disk) check forced happens so I went to my crond.pid file to change the 30 to 50 but my cron file only has "8159" in it, help me.

---

### Post by Zelut on 2006-03-16
Then .pid file isn't the one that you want to edit.  That is the processor ID file, so that wont help you change the settings.

It doens't sound like its a cron job because its not on a schedule, but per x number of boots.  You've got me curious now as to where that is.. I'm going to look around & see if I can find it.

If anyone else knows...

---

### Post by rfruth on 2006-03-16
No .pid, thanks Utah team !

---

### Post by Zelut on 2006-03-17
I've found a few things for you.  The tune2fs (assuming you're using ext3 or ext2 filesystem) can set a check by $time or by $mount.

> If you're using ext2 or ext3 filesystems you can use this command to
disable all checking:

tune2fs -c -1 -i 0 <partition>
check out 'man tune2fs' for details on the settings you can change here.  The -c & -i are both variables that can change the number of boots/days between checks.

> sudo touch /fastboot
this should remove it all together.  Not 100% on this however.

---

