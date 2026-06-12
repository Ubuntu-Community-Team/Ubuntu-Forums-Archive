---
title: "pgadmin3 crashes on Kubuntu breezy"
date: 2005-11-13
forum: Desktop Environments
---

### Post by vitorsouza on 2005-11-13
Hi there,

I installed package pgadmin3 and when I try to run the program, it crashes. Looking up the net I found out it's a GTK-QT problem: 

From [http://www.pgadmin.org/pgadmin3/faq/#gtk-qt](http://www.pgadmin.org/pgadmin3/faq/#gtk-qt):

[I]**Crash on Linux: Qpixmap: Invalid pixmap parameters**
When running on a machine with gtk-qt-engine installed, pgAdmin III will crash with a segmentation fault. A console will print "QPixmap: Invalid pixmap parameters".This is caused by a broken gtk-qt-engine; not only pgAdmin III suffers from this. To fix, remove the broken gtk-qt-engine or install a fixed version if available.[/I]

Is it true that Kubuntu's gtk-qt-engine is broken? Is a fix expected soon?

Thanks,

Vitor Souza

---

### Post by gvalenzu on 2006-01-11
I had the same problem and I solved unistalling the packege *gtk2-engine-gtk-qt*, wich made gtk aplication looks like KDE.

---

### Post by vitorsouza on 2006-01-11
[QUOTE=gvalenzu]I had the same problem and I solved unistalling the packege *gtk2-engine-gtk-qt*, wich made gtk aplication looks like KDE.[/QUOTE]

Yes, I've done the same, but that is far from ideal...

---

### Post by peholmst on 2006-01-25
I've read somewhere that this bug has been fixed in qt-kde 0.60.1. I guess we'll just have to wait until the packages are updated...

-Petter-

---

### Post by nuscly on 2006-02-15
I solved this problem without uninstalling gtk-qt :

You might change the theme, and choose a native gtk2 theme in kde control panel, gtk-qt style and font. Instead of "Use my KDE style in gtk apps", select a gtk2 theme. 

You could install new theme with package with name that starts with gtk2-engine. In all the theme available, you could find the theme the most closed to the qt theme used in kde application.

That's might correct also other bug in :D wxwidget  or wxwindows graphic crash.

---

