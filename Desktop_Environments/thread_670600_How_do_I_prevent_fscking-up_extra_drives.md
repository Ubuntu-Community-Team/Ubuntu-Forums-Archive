---
title: "How do I prevent fscking-up extra drives?"
date: 2008-01-17
forum: Desktop Environments
---

### Post by mount_evans on 2008-01-17
Every time I boot, fsck takes a long time to scan one of my tertiary FAT32 drives.  It must find errors, because there are about 20 files named "fsck" in the root directory.  Sometimes fsck fails so badly that it stops the boot process.  I looked at some of the fsck files and one of them is a portion of a jpeg.  I figure Ubuntu must be doing something to the files on this drive, or the result of the fsck would be the same each time.  I don't like this.  This drive was fine before I installed Ubuntu on my secondary drive, and I would rather Ubuntu just left it alone.  I also don't want Ubuntu messing up my primary (Windows) drive, though I would be like to be able to read from it.  If Ubuntu wants to fsck around with the Ubuntu drive, OK; but how do I get it to leave my other drives the fsck alone?

Put another way, the only drive Ubuntu should fsck with is the drive it is on, /hdb (i.e., it can go fsck itself.)  How do I exclude all others?

---

### Post by ajgreeny on 2008-01-17
Find the reference to it in /etc/fstab (hda?) and change the last two figures in that to 0 0 (zero and zero), though you should make sure that the fault in the file system is sorted as well, perhaps using checkdisk, scandisk, or something similar in windows.  You will need to edit as root so ```
gksudo gedit /etc/fstab
```and go from there.

---

### Post by mount_evans on 2008-01-17
> **ajgreeny said:**
> Find the reference to it in /etc/fstab (hda?) and change the last two figures in that to 0 0 (zero and zero), though you should make sure that the fault in the file system is sorted as well, perhaps using checkdisk, scandisk, or something similar in windows.  You will need to edit as root so ```
gksudo gedit /etc/fstab
```and go from there.

I'll go look for it.  Uh, how does one "comment out" code in an fstab file?

---

### Post by ajgreeny on 2008-01-18
You won't need to comment out the line, unless you want to stop windows mounting at boot time, you simply need to change the final figure to zero.  However, to answer your question, you simply add a # to the line you want ignored.

---

### Post by El_Belgicano on 2008-01-18
Hello,
My laptop is also running that dosfsck on my FAT32 partition, but not encoutering any errors.
I read somewhere on the forums that it is wiser to let the check happen, but I prefer a faster bootup and run the check once every 30 bootups for example...
is there someway to achieve this, or a command tu run that dosfsck from the terminal?

---

### Post by nkobel003 on 2008-01-19
as  ajgreeny said:
```
gksudo gedit /etc/fstab
```

it would be wise to check the script when your laptop boots up and see which hard drive exactly is taking so long to check, for example, it might look something like this
```
dofsck 2.11 DATA....
dev/hda1....
```

upon finding the drive that wants to be scanned, change the second parameter in the fstab to 0 under hda1.

---

### Post by El_Belgicano on 2008-01-19
@nkobel003:
thnx, i'll swtich that in the evening, and do you know a command that I can run to make that dosfsck from a Ubuntu terminal. Just because I'm switching less and less to my windows partition and it would be frustrating just to boot up in XP to run a filesystemcheck that I could do from Ubuntu....

---

