---
title: "Changing desktop background kills Firefox"
date: 2005-05-03
forum: Desktop Environments
---

### Post by NTolerance on 2005-05-03
That's right.  I can duplicate this problem every time.  This happens either by manually changing my background via the KDE Control Center or enabling the desktop background slideshow.  Every time the background changes Firefox just disappears.  Can anyone else duplicate this?  Any ideas?

---

### Post by Narg on 2005-05-03
That happens with me, and firefox disapears when I look at an empty virtual desktop. It doesn't always happen, but it happens alot.  I can reproduce it every time, but in a few tries I can :)

Firefox on kubuntu is wierd.

It happens on binary stable firefox, compiled firefox, recent nightly firefox binary, and the .deb package on firefox in the repos.


*mutters*

---

### Post by NTolerance on 2005-05-13
After doing some testing, it appears that this problem may be caused by the gtk-engines-gtk-qt package.  I had formatted the other day and reinstalled Kubuntu.  I noticed that I had not experienced this problem until after I had installed gtk-engines-gtk-qt.  In the end I'd rather have Firefox actually stay open instead of some slightly better-looking GTK apps.

---

### Post by jeremy on 2005-05-13
I have gtk-engines-gtk-qt & firefox from the repos,, but this does not happen to me.

---

### Post by NTolerance on 2005-05-13
[QUOTE=jeremy]I have gtk-engines-gtk-qt & firefox from the repos,, but this does not happen to me.[/QUOTE]

Did you install from the Ubuntu or Kubuntu CD?

---

