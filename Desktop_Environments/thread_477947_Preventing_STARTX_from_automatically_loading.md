---
title: "Preventing STARTX from automatically loading"
date: 2007-06-18
forum: Desktop Environments
---

### Post by abasel on 2007-06-18
I installed the GUI on my server but don't want the box to boot to the GUI automatically.

I've change the runlevel to 3 (I think) but the PC still boots to the GUI login. How do I force it to boot to the text login screen?

---

### Post by yabbadabbadont on 2007-06-18
Uninstall gdm or kdm or whichever graphical login manager is installed.  Alternatively, remove the symbolic links in /etc/rc?.d directories that start them up at boot time.

---

