---
title: "full taskbar semi transparent"
date: 2008-03-14
forum: Desktop Environments
---

### Post by guimenez on 2008-03-14
hello.

i want to make whole taskbar semi transparent. i know i change choose a cooler an put it transparent, but i want to put the taskbar theme transparent(png icons) is it possible?
if a make the color trnasprency, there are some icons that won't be transparency.

thanks

---

### Post by Deadheded on 2008-03-14
Yes, right click on the taskbar and go to properties.
 
Click the backround tap and then the Solid Color button.  You can then use the slider to control transparency

---

### Post by mcduck on 2008-03-14
Some GTK themes don't work well with transparent panels, as they us bitmap images for panel backgrounds and for panel buttons. That's the problem in the screenshot you posted.

Usually the easiest way is to just try to find some theme that doesn't have this problem, at least all Clearlooks, Ubuntulooks and Murrine-based themes should work fine.

If you really want to use just that theme, then the only way would be to try editing it's gtkrc file to get rid of all pixmaps on panels.

---

