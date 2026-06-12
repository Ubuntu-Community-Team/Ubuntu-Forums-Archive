---
title: "Dolphins places"
date: 2010-04-24
forum: Desktop Environments
---

### Post by naja on 2010-04-24
Hi
is there a way to rename items in the places-sidebar? i mean the one for mountend harddrives, the names are too long e.g. "X.Z GiB Hard Drive" what cauese them to be scaled down to allow caption to fit in. i would like to make the names smaller e.g. "C" so the icons can be scaled up again.
thanks

---

### Post by Alan James on 2010-04-24
After adding the location to the places panel just right click on the icon and click “Edit.” Change the “description” and it will rename it. Very simple.

---

### Post by naja on 2010-04-25
Hi
thank you for your reply but this does not work on mounted devices only folders imho.

---

### Post by benerivo on 2010-04-25
I think Dolphin looks for a device 'label' to use, and if there isn't one then it just uses the size of the drive to name it by. You can label a drive with...```
e2label <device> <name>

eg.
e2label /dev/sda5 Music
```...which has to be done as root, and you can reboot for it to work.

---

### Post by naja on 2010-05-01
hi
thanks for answering but e2label works only on ext2/ext3 drives.
any otherway? maybe editing the fstab file?

---

### Post by benerivo on 2010-05-01
If your drive is ntfs, then you could try ntfslabel as described here...

[http://linux.die.net/man/8/ntfslabel](http://linux.die.net/man/8/ntfslabel)

I don't have any ntfs drives so i haven't tried it myself.

---

### Post by naja on 2010-05-01
found it !!!
use ntfslabel instead

---

