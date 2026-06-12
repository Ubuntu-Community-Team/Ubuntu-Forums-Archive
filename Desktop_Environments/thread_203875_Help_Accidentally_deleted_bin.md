---
title: "Help: Accidentally deleted /bin"
date: 2006-06-26
forum: Desktop Environments
---

### Post by miceagol on 2006-06-26
This is kind of hilarious, but I deleted /bin by mistake. I had an old suse-distribution on my external HD, that I started removing. But the command ```

rm -r /bin

```
deleted the one of my system instead, even though I was in the relevant folder. Should have dropped the slash. ](*,) 

Anyway, I booted with the Live CD, and copied all the files in the /bin-folder on the CD to the one on of my system, but there are still files missing during boot:
```

INIT: cannot execute /etc/init.d/rcS
INIT: Entering runlevel: 2
INIT: Cannot execute /etc/init.d/rc

```
And then the boot sequence stops, unless I push CTRL+ALT+DEL.

Is there anything I can do to restore the files of my /bin-folder without reinstalling Ubuntu? I tried writing rescue in the "alternative options"-window when starting from the Ubuntu CD, but nothing happened. :(

---

### Post by rai4shu2 on 2006-06-26
It's probably not possible to restore /bin without a backup or reinstall of some kind. If you can, you should install onto some unused partition or hard drive, or move your data to a temporary partition somewhere while you reinstall.

---

