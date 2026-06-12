---
title: "Adding panel applets?"
date: 2010-03-25
forum: Desktop Environments
---

### Post by tica vun on 2010-03-25
I'm trying to add some panel applets on UNR, but the panel seems to be locked (can't do anything with it in right-click menu. What to do?

Edit: to clarify, the "move", "remove from panel" and "locked" buttons in the right-click menu are greyed out.

Edit2: So I've managed to get to the panel's context menu itself by killing the window-picker applet process, and it turns out the "add to panel" and "new panel" buttons are greyed out too. What is this?

---

### Post by Fxy on 2010-03-25
Have you tried killing the gnome-panel and then relaunching it :?

Load terminal and type > killall gnome-panel  Gnome panel should relaunch itself, if not type > gnome-panel in terminal...

---

### Post by tica vun on 2010-03-25
Yeah, killing it makes it relaunch by itself, but I still can't add anything to it.

---

### Post by Fxy on 2010-03-26
Emmm im no expert on this type of stuff, but what if you were to install an x winow manager like openbox or something and then try launching gnome-panel through that to see if you still have the same problem...

---

