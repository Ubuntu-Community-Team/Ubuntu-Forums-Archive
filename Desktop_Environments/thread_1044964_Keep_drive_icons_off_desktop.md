---
title: "Keep drive icons off desktop"
date: 2009-01-19
forum: Desktop Environments
---

### Post by ledlincoln on 2009-01-19
I'm running Gnome.  If a CD/DVD/USB drive is inserted, a big icon for it appears on my formerly pristine desktop.  Can I set a preference to have them not appear on the desktop?  I still want them to appear in the upper panel.

---

### Post by Yashiro on 2009-01-20
[http://ubuntuforums.org/showthread.php?t=193470](http://ubuntuforums.org/showthread.php?t=193470)

---

### Post by ledlincoln on 2009-01-22
Nope, that doesn't seem to be how Intrepid works.  fstab lists my CD/DVD drives, and I changed them to point to /mnt, but it was ignored, even on reboot.  The external USB drives are not even in fstab.

---

### Post by mcduck on 2009-01-23
Press Alt-F2 and run "gconf-editor". Use that to browse to apps/nautilus/desktop and disable the "volumes_visible"-key. :)

(editing fstab to mount drives to /mnt is used if you want to keep CD and USB drive icons on desktop, but also have some internal drives that you don't want on your desktop)

---

### Post by ledlincoln on 2009-01-23
Thank you, McDuck!  That's exactly what I want.  Now my desktop artwork is not defaced (it's currently displaying a work by Dali).

---

### Post by boolander on 2010-02-05
it helped me too... thanx

---

