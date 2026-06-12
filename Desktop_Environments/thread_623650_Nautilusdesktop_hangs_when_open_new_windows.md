---
title: "Nautilus/desktop hangs when open new windows"
date: 2007-11-26
forum: Desktop Environments
---

### Post by speakman on 2007-11-26
I seems to have a very strange problem which I can't understand nor figure out what caused it.

When the system starts up, it's all fine. All desktop icons are shown on the desktop and is "clickable".
But as soons as I try to open a folder, either through desktop icon or through the menue, it all locks.
All desktop icons disappear (as soon as I drag something over them, like a window), no folder is opened and the desktop as whole is no longer usable.

If I kill the bonobo-activation-server, the folder opens up but the desktop is still lost.

I use Gutsy with an Nvidia graphic card with proprietary drivers. Compiz is not used.

Anyway to track this down?

---

### Post by cwmaxson on 2007-11-27
I'm having a similar conflict between nautilus and bonobo.  Does anyone know about this?

---

### Post by speakman on 2007-12-04
By doing this I can now open windows and logout correctly, but the desktop is totaly missing:
```
$ gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```
The system runs a bit more stable, but what's really causing it is still a big mistery.
And again, the desktop icons is totaly gone with this...

---

