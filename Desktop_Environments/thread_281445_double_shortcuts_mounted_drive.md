---
title: "double shortcuts mounted drive"
date: 2006-10-21
forum: Desktop Environments
---

### Post by grilkip on 2006-10-21
Hi, I've added two lines to my fstab to mount my windows partitions.```
dev/hda1    	/media/windows1	ntfs  	nls=utf8,umask=0222 0    0
dev/hda2    	/media/windows2	ntfs  	nls=utf8,umask=0222 0    0
```After doing this, when I try sudo mount -a it complains the devices do not exist.

However...

After rebooting they are mounted, but now I've got 4 shortcuts on my desktop instead of 2.```
windows1
windows2
windows1(2)
windows2(2)
``` The extra ones keep coming back after rebooting or unmounting, how do I get rid of them?

---

### Post by grilkip on 2006-10-21
I'm using edgy btw

---

### Post by grilkip on 2006-10-23
HELP! :cry:

---

