---
title: "kubuntu-desktop killed GNOME"
date: 2006-08-25
forum: Desktop Environments
---

### Post by _profox on 2006-08-25
I installed kubuntu-desktop last night to try some things in KDE.
But now I can't get back to GNOME. GNOME crashes and its theme looks really weird. Sometimes I am able to get a blank gnome-panel -- sometimes nothing at all

Could this be an issue with gtk-qt-engine ? but I can't disable that ? ...

---

### Post by jimbren on 2006-08-25
does it return an error?  have you tried to reinstall gnome-desktop?

---

### Post by _profox on 2006-08-25
No.

It was what I suspected. A bug that should already be fixed.
I worked around it by deleting: ~/.gtkrc-2.0

Bug: [https://launchpad.net/distros/ubuntu/+source/gtk-qt-engine/+bug/36256](https://launchpad.net/distros/ubuntu/+source/gtk-qt-engine/+bug/36256)

---

### Post by jimbren on 2006-08-25
I'm glad you were able to figure it out.  I never look in the bug reports...I'll have to start.

---

