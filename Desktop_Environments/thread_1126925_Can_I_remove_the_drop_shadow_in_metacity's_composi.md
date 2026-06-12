---
title: "Can I remove the drop shadow in metacity's compositing manager?"
date: 2009-04-15
forum: Desktop Environments
---

### Post by spiritfox on 2009-04-15
I was having problems with compiz, so I disabled it and switched over to metacity's compositing manager.  the one thing I've noticed that I don't like is the fact that metacity puts a drop shadow on every window.  This includes the conky window, which I want to look integrated into the desktop.  Is there a way to disable the shadow for individual windows or even for all windows that would still allow me to use docky/other themes for GNOME Do and other compositing features?

---

### Post by kawaji on 2009-04-16
I think parameters for drop shadow are hard-corded and you need to edit source files of metacity or something.

**Xcompmgr** seems to have more configurable options.
[This link]("http://www.kabatology.com/02/22/gcompmgr-graphical-front-end-for-xcompmgr-composite-window-manager/") might be your help.

---

### Post by spiritfox on 2009-04-16
Thanks a lot.  xcompmgr seems like the perfect solution.

---

### Post by mrneil on 2011-04-21
Use gconf-editor to uncheck the compositing_manager option under apps->metacity->general.

---

