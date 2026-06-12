---
title: "[SOLVED] GUI Scan Disk"
date: 2008-03-18
forum: Desktop Environments
---

### Post by Rytron on 2008-03-18
Is there any GUI Scan disk utility in the works for Ubuntu?

---

### Post by NightwishFan on 2008-03-18
Search for a front end to Fsck. Although I do not see the point really.

---

### Post by ajgreeny on 2008-03-18
You can't use fsck on a mounted partition so there is little point in having a gui that you can't run to check your system anyway.  You could use it for other unmounted partitions, I suppose, but how long does it take to type just a few words ```
fsck /dev/hda*
``` in the terminal and use fsck on the unmounted partitions?

---

### Post by jimcooncat on 2008-03-18
You really don't have the same issues here that ScanDisk tried (and not so well) to fix with the FAT16 and FAT32 filesystems it was developed for. The filesystems in use are much smarter at keeping your data safe and available. Better that your focus is on other parts of your storage setup: your hard disk health and backups.

If you want to be notified that there's a hard disk failure going to occur:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

I use rsnapshot for backups from one computer to another. I keep a whole week's worth of changes. If one of my users deletes something and lets me know, I can very easily get it back for them.
[http://www.inmostlight.org/2006/03/easy-backups-with-rsnapshot](http://www.inmostlight.org/2006/03/easy-backups-with-rsnapshot)

---

