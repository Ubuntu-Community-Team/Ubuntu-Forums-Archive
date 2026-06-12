---
title: "Remove samba icons from desktop?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by thebinz on 2006-09-24
So i mounted my network drives with samba which automatically placed icons on my desktop (Gnome 2.14.3). How do i go about removing the desktop icons without unmounting the network drives?

I searched the forum but only found how to remove them from KDE - [link ]("http://ubuntuforums.org/showthread.php?t=113733&highlight=remove+samba+icon")


//Phil

---

### Post by pete on 2006-09-24
This thread did it for me:

[http://www.ubuntuforums.org/showthread.php?t=258415](http://www.ubuntuforums.org/showthread.php?t=258415)

Also, I *seem* to recall that only stuff mounted in /media shows up as desktop icons.  You could try modifying your fstab to put the mount-point somewhere else (assuming they're mounted in /media).  Not positive on that one, though.

---

### Post by thebinz on 2006-09-24
Perfect. 

Thank you pete. ;)

---

