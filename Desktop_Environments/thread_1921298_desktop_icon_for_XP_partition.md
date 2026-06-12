---
title: "desktop icon for XP partition"
date: 2012-02-06
forum: Desktop Environments
---

### Post by ieee488 on 2012-02-06
Is there a way to have the icon for the XP partition show up on the desktop?

The partition is mounted.

---

### Post by ajgreeny on 2012-02-06
There certainly is;  I just can't remember exactly where the setting is, but I think it is in the desktop configuration somewhere, and you set the system to show "Volumes" on desktop, not partitions, which may be why you have missed it in the past.

I don't think you can choose which volumes to show; it is all or nothing.  If you want only the XP partition to show, you may have to make a launcher for it yourself, and place it on the desktop manually.

---

### Post by ieee488 on 2012-02-06
Thanks.

I went to Applications Menu -> Settings -> Desktop, but there wasn't an option for either volumes or partitions.

Looks like it isn't available in xfce.

---

### Post by GraeW on 2012-02-07
There is a way to show mounted volumes in xfce - I will have to check the right path when I get home as I don't have my laptop with me at work. It may not be what you are looking for though; as stated above, I don't recall that it will differentiate between different volumes, but I will check it when I can.

---

### Post by GraeW on 2012-02-07
It is there under XFCE .. open up the menu, go to Settings --> Desktop.

there are three tabs on this window. The third one is "Icons" .. in there you can select Home | Filesystem | Trash | Removable Devices.

I am not sure if the system will recognize your XP partition as a "removable device" but it might, and that would be how to enable a link on your desktop. I know it *did* work for me.

---

### Post by ajgreeny on 2012-02-08
Surprisingly, I think, as they are not really removable drives, GraeW has got it right.  That tick box enables and disables all volumes/partitions in the computer.  Seems a very odd description to me, as there is no way I can remove the volumes physically short of deleting the partitions.

We are also correct in saying that it is all or nothing.  You can not choose which partitions show on the desktop.

---

