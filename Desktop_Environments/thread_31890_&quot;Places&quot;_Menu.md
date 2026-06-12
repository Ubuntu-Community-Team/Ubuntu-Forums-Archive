---
title: "&quot;Places&quot; Menu"
date: 2005-05-05
forum: Desktop Environments
---

### Post by markr on 2005-05-05
I would like to add my Windows C: (NTFS) and D: (Fat32) partitions to the "places" menu or the "Computer" menu so I don't need to navigate to /media to get to them.

I've searched the forums, but nothing seems to suggest that this can be done.  I've added the partitions to my fstab file (see below), but they are still only accessable by navigating to /media.


/dev/hdc2       /media/c      ntfs       umask=0222       0          0
/dev/hdc3       /media/d     vfat       umask=000          0         0

---

### Post by Fab on 2005-05-05
[QUOTE=markr]I would like to add my Windows C: (NTFS) and D: (Fat32) partitions to the "places" menu or the "Computer" menu so I don't need to navigate to /media to get to them.

I've searched the forums, but nothing seems to suggest that this can be done.  I've added the partitions to my fstab file (see below), but they are still only accessable by navigating to /media.


/dev/hdc2       /media/c      ntfs       umask=0222       0          0
/dev/hdc3       /media/d     vfat       umask=000          0         0[/QUOTE]
 heres how i did it:
in any gtk file open/save dialogue, mark the /media/c folder on the right side and hit "add" on the left bottom, it should then appear in the list to the left, which is apparently the first part of the places menu

---

### Post by Xgkkp on 2005-05-05
Where does it actually store the places links? I'd like to rename the entries on my places

---

