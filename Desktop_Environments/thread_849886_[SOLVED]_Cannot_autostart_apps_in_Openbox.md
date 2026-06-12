---
title: "[SOLVED] Cannot autostart apps in Openbox"
date: 2008-07-05
forum: Desktop Environments
---

### Post by Inxsible on 2008-07-05
I created a autostart.sh file under ~/.config/openbox

and added ```
conky &
(sleep 2 && fbpanel) &
``` But none of these programs start up when I log in. What am I missing ?

---

### Post by urukrama on 2008-07-05
Do you have *#!/bin/sh* at the top of that file? Did you make the file executable (*chmod +x ~/.config/openbox/autostart.sh*)?

Note also that the Openbox autostart file will not be used if you use Openbox as the window manager of a desktop environment (Gnome, KDE, XFCE). If you use Openbox within a DE, you'll need to use the autostart/session management of the DE.

---

### Post by sayakb on 2008-07-05
Probably you miss the **#!/bin/sh** at the top of the file.

EDIT: Oh sorry, didn't read post #2 ;)

---

