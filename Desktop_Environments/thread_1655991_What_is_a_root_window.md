---
title: "What is a root window?"
date: 2010-12-30
forum: Desktop Environments
---

### Post by MichaelBurns on 2010-12-30
Simple question (but I hope for an elaborate answer): What is a root window?

E.g., the **-root** argument to the **xwininfo** command gives me information about the "root window".

Particularly, I want to understand the difference between the root window and the Desktop window.  How do I use it?  Why do I need to be aware of it?  What problems can I solve by using it?  etc.

---

### Post by germanix on 2010-12-30
All you want to know about "Root" you will find here:
[http://www.linfo.org/root.html](http://www.linfo.org/root.html)

---

### Post by mcduck on 2010-12-30
Interestingly, the link doesn't actually explain root window... ;)

Anyway, the root window the first graphical window, covering your screen and serving as the base on top of which all graphical applications draw their windows.

It's not really anything useful if you are using a desktop environment like Gnome or KDE, since they draw their desktops on top of the root window, so you'll never even see it.

If you use a simpler window manager, like Openbox, the root window will still be visible, and you can for example place a image there to serve as your wallpaper image.

---

