---
title: "Random Mouse Pointer"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Enkidu on 2005-04-09
When Gnome loads, it initially shows the default X picture for the mouse, then the actual mouse point comes up but the X stays on the screen in the very center on top of all the applications.  The mouse moves the pointer independly of the X which will not go away.  Any idea what would cause this?

---

### Post by kassetra on 2005-04-09
[QUOTE=Enkidu]When Gnome loads, it initially shows the default X picture for the mouse, then the actual mouse point comes up but the X stays on the screen in the very center on top of all the applications. The mouse moves the pointer independly of the X which will not go away. Any idea what would cause this?[/QUOTE]

Errors in the video driver, actually - 
Here's how to get rid of it:
1. Open a terminal: Applications->System Tools->Terminal
2. Type this:
 ```
sudo gedit /etc/X11/XF86Config-4
``` and press enter.
3. When it opens, scroll through until you see a 'device' section - and add:
 ```
Option	"HWCursor" 	"off"
``` 
4. Save & Close
5. Reboot.  :)

---

