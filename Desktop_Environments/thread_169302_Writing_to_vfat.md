---
title: "Writing to vfat?"
date: 2006-05-02
forum: Desktop Environments
---

### Post by ELD on 2006-05-02
Hi all i have my vfat partition mounted fine and i can view the files but i cannot write to this partition.

Any ideas why?

---

### Post by aysiu on 2006-05-02
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by tsrjzq on 2006-05-03
use sudo or set mount umask as 000 in fstab.

---

### Post by dcstar on 2006-05-03
[QUOTE=ELD]Hi all i have my vfat partition mounted fine and i can view the files but i cannot write to this partition.

Any ideas why?[/QUOTE]
My /etc/fstab has this line which allows R/W:
```
/dev/hda1       /c		vfat    	umask=000,noatime,auto			0       0
```

---

### Post by ELD on 2006-05-07
[QUOTE=dcstar]My /etc/fstab has this line which allows R/W:
```
/dev/hda1       /c		vfat    	umask=000,noatime,auto			0       0
```[/QUOTE]

I am now using what you posted, altho if i still try to copy anything onto my partition then it says i don't have permission?

---

### Post by Sutekh on 2006-05-07
I would have recommended the method in the link aysiu posted.  Doubly so, as it shows you how to re-mount the FAT partition again with the new settings.

---

### Post by ELD on 2006-05-08
[QUOTE=Sutekh]I would have recommended the method in the link aysiu posted.  Doubly so, as it shows you how to re-mount the FAT partition again with the new settings.[/QUOTE]

Thanks it is working now!

---

### Post by ELD on 2006-05-15
[QUOTE=ELD]Thanks it is working now![/QUOTE]

Hey guys accidently edited the options in fstab for my swap file, what is the defualt line for a swap file?

Thanks!

---

### Post by Sutekh on 2006-05-15
The default entry for swap is like this
```

/dev/hda5    none    swap    sw    0    0

```
If your swap is the partition /dev/hda5 of course.

---

