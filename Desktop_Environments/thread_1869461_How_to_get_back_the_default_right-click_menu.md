---
title: "How to get back the default right-click menu?"
date: 2011-10-25
forum: Desktop Environments
---

### Post by kuric on 2011-10-25
Hi guys,

I've changed the default desktop right-click menu in Lubuntu (LXDE environment), by clicking the last option that was in it, I think.
Now I don't have the option to create new items and folders.
These are the only options I get when I right-click on the desktop:
-Terminal Emulator
-Web Browser
-Desktops
-ObConf
-Reconfigure
-Restart
-Exit
How do I revert this and get back the default menu?!
Thank you!

---

### Post by kuric on 2011-10-25
Ok, solved.

I went to the terminal and did this:

$ pcmanfm --desktop-pref

Advanced tab > Removed the mark on show the window manager...

---

### Post by muppet317 on 2011-11-18
Thanks! So simple - I've been hunting around for something to get back the default desktop context menu

---

