---
title: "XMonad: un-removable gray windows at startup"
date: 2012-05-16
forum: Desktop Environments
---

### Post by sharshofski on 2012-05-16
I just upgraded my netbook to 12.04 and decided it would be fun to try XMonad. I'm running XMonad + GNOME. Everything works great out of the box... except...

Three panels appear at startup: the desktop and two gray panels (as shown on the right in the screenshot). **I can't remove/close the two gray panels** with ctrl+shift+c. And I can't fill them with applications/windows. So they're just pointless. Why?? What am I doing wrong? How can I get rid of them? Augh!

I've been moving the two gray panels to another workspace and ignoring them, but I'd rather understand what's going on.

Any help appreciated!

---

### Post by ckop64 on 2012-05-16
Post your xmonad.hs

---

### Post by sharshofski on 2012-05-18
I just grabbed one of the templates from the XMonad site to start with. I couldn't find anything in there that seemed related.

I figured out part of why the gray panels showed up: I selected the  "GNOME and XMonad" option at login. When I run ```
pkill gnome-panel
```the two gray panels disappear. And running  ```
gnome-panel &
``` brings them back. So clearly GNOME and  XMonad aren't meshing well at startup. Does anyone know why this is  happening in the first place?

---

