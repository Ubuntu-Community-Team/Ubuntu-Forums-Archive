---
title: "Gnome Desktop: Hiding Partitions, but not Removable Media"
date: 2007-04-10
forum: Desktop Environments
---

### Post by jketvirtis on 2007-04-10
Hi there.

I was having a minor problem with GNOME and its desktop.  I would like to be able to hide my partitions (hda1, hda2) from displaying on the desktop, but keep removable media (such as USB sticks and CDs) showing up there as they had before.  I found the gconf key for hiding volumes, but that is an all or nothing approach.  I suppose I could unmount the partitions, but I would rather they just not show up on the desktop but still be in "computer:/".

Any help would be great.  Thanks.

---

### Post by dfreer on 2007-04-10
try remounting them in a different folder than /media (mine is mounted /localhd), and then change that gconf key back to it's default so that the USB drives display normally should do the trick.

---

### Post by ComplexNumber on 2007-04-10
i wouldn't mind it being like that too, but it doesn't really bother me enough to want to see some sort of hack or workaround. i would like the removable media to show up when they are plugged in, but unfortunately, it also displays other drives that are permanently attached (ie it displays all mounted  drives).

when you plug in the USB or insert a cd ito the drive, a nautilus window pops up with the contents of that removable media. that saves me from having to go into Computer.

i can't think of a convenient and elegant solution  off hand.

EDIT: the above poster may have a point because it displays drives that appears in the /media folder. you would need to adjust your fstab file to reflect the different mount point location.

---

### Post by dfreer on 2007-04-10
From what I understand of it Gnome only puts shortcuts to harddrives/partitions located in /media.

---

### Post by jketvirtis on 2007-04-10
Thanks for the help!  I'll give that a try when I get home, though I have to say that in this instance I really prefer KDE's ability to highly customize just what shows up on the desktop.  But that's neither here nor there.  Thank you!

---

### Post by ComplexNumber on 2007-04-10
> **jketvirtis said:**
> Thanks for the help!  I'll give that a try when I get home, though I have to say that in this instance I really prefer KDE's ability to highly customize just what shows up on the desktop.  But that's neither here nor there.  Thank you!
as a suggestion, you could unmount(_ALWAYS_ unmount a device first before attempting to change it in any way) and then delete the link to the mount points in /media. then adjust your fstab so that it points to /mnt instead of /media. then create the mount points in /mnt and then mount them.

---

