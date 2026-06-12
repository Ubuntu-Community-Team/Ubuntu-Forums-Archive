---
title: "How to enable destop effects (compositting) in KDE 4"
date: 2008-11-01
forum: Desktop Environments
---

### Post by ksamanta on 2008-11-01
Whenever I enable the desktop effects, my screen goes blank forcing me to hit Ctl+Alt+Backspace to quit. If I try to login again, the screen first becomes blank white and then dark, and I cannot see anything on the screen. But if I disable compositting in the ~/.kde/share/config/kwinrc file using a failsafe terminal, then I can login to KDE again and everything looks OK (but no desktop effect). How do I enable the desktop effects in KDE? 

I am using Intrepid Ibex (Ubuntu 8.10), my desktop manager is GNOME (i.e., GDM) and I prefer to use KDE as my window manager. Compiz effects (e.g. cube rotation) work perfectly under GNOME. I want to have similar effects in KDE too.:confused:
Any help will be greatly appreciated!

Thanks!

---

### Post by ksamanta on 2008-11-01
OK, I found a working solution: Use XRendR instead of OpenGL as the compositing type.In case others also have the same problem, this option can be found here
```
 sytemsettings > Desktop Effects > General (tab) > Advanced Options 
```:popcorn:

However, it seems that I have to wait until kde 4.2 in order to use the cube in kwin.

---

