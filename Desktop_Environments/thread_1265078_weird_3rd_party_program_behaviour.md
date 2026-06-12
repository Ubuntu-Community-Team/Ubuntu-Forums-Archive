---
title: "weird 3rd party program behaviour"
date: 2009-09-13
forum: Desktop Environments
---

### Post by gax908 on 2009-09-13
whenever i turn on blender, the window seems to blend in with the desktop and sectioned when other windows appear.

could it be the graphics card? mines an intel GMA.

i dont think i can describe it in words...so heres a picture of the problem.

here's blender....or whats left of it.

other than this problem i enjoyed ubuntu.

[http://picasaweb.google.com/lh/photo/255otXwInCR5Q07BdLG7zg?feat=directlink](http://picasaweb.google.com/lh/photo/255otXwInCR5Q07BdLG7zg?feat=directlink)[IMG]http://picasaweb.google.com/lh/photo/255otXwInCR5Q07BdLG7zg?feat=directlink[/IMG]

---

### Post by mcduck on 2009-09-13
Blender uses OpenGL to draw it's interface, and this might cause problems when running Compiz (which also uses OpenGL).

My suggestion is to run "metacity --replace" before starting Blender to switch to normal window manager, and then when you are done with Blender run "Compiz --replace" to get Compiz back again.

There's also some notification area icon available that allows easy switching between window managers, but I wouldn't bother since if you run those comamnds though the run dialog (opened by pressing Alt-F2" it will remeber then and you'll only need couple of key presses to switch between Metacity and Compiz, so no need to install extra programs for that. :)

(The important thing is that you shouldn't toggle Compiz on and off through System/Preferencs/Appearance, or you'll loose your custom Compiz configurations as the Visual Effects-options there switch between Metacity and two pre-configured Compiz setups instead of your own Compiz configuration)

---

### Post by gax908 on 2009-09-17
thanks

---

