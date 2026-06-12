---
title: "5% of my disk drive was missing"
date: 2005-05-23
forum: Desktop Environments
---

### Post by ioliver on 2005-05-23
OK, this is probably something that everyone except me knew, but ext2/3 filing systems reserve 5% of the disk for use by root as a default.

I found this when I couldn't make the results from "df -h" add up!

Anyway, if you do -
"tune2fs -m 0 /dev/hda" (or whatever you drive letter is)
you will get this 5% back. You might want to reserve some space for root (the above command leaves root fighting on equal terms!) but I was doing this for raid arrays used just for data.

I got 37GBytes back with a single command!

Note that the tune2fs man page says that you shouldn't use it on a mounted hd, so you might want to boot in single user mode. I didn't bother as setting this reserved percentage seems fairly benign.

Ian

---

### Post by N'Jal on 2005-05-23
Um i don't know this for sure but everytime i use a file system tool fsck etc it has to be on an unmounted fs else it can damage it. Don't know for sure in your case

---

