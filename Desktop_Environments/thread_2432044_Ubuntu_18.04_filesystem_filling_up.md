---
title: "Ubuntu 18.04 filesystem filling up"
date: 2019-11-26
forum: Desktop Environments
---

### Post by giobaxx on 2019-11-26
Hello guys

I'm facing a strange problems, in an ubuntu 18.04 i have the disk full, and if i run ***df -h*** i see that i'm using 100% of the disk, but if i run **du -h /  --max-length=1 **i see that the disk is about **600 GB of 3 TB**( there is only the /partition )**.** I saw  the same using the [FONT=Arial, Helvetica Neue, Helvetica, sans-serif][COLOR=#242729]Disk Usage analyzer.[/COLOR][/FONT]

[FONT=Arial, Helvetica Neue, Helvetica, sans-serif][COLOR=#242729]Anyone of you can tell me to understand what is happening? [/COLOR][/FONT]

[FONT=Arial, Helvetica Neue, Helvetica, sans-serif][COLOR=#242729]i have googled it the problem and i try to run thins command [/COLOR][/FONT]***sudo lsof | grep 'deleted' ***thatare, from what i have understood, deleted files but still present on the disk and from the output of this command we can see  a list of file that however i don't know how to delete. These could be the ones causing the problem?

At the end the problems was solved rebooting the Workstation, this has deleted all these 'cached files', but i would like to understand what caused this problem....:confused:

---

### Post by ajgreeny on 2019-11-26
Keep an eye out for this happening again and if it does can you show us the output of ```
du -h -d 1 | sort -h
``` which will show us where in the filesystem all that space is being used; my bet would be a runaway log of some kind in /var/log but let's look a bit further.

---

### Post by giobaxx on 2019-11-26
Using *du* command there is'nt any specific big file/folder. *Home Folder* was about 560 GB and it was the biggest. I've checked */root* and */var* if there was some strange big file, but nothing. But if you run *df -h* you stll saw the / partition full, 100% of the disk used.

If there was some hidden/cached files i really don't know where to look for.

---

