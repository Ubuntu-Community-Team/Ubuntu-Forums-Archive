---
title: "Autostart beryl only with xgl?"
date: 2006-11-29
forum: Desktop Environments
---

### Post by zero gravity on 2006-11-29
Im running xgl and beryl on edgy 32 bit.
When I log in I can chose to log in with xgl.
But my question is, is there a way to make beryl-manager load only when i log in with xgl? (meaning not with sessions)

---

### Post by wglenncamp on 2006-11-29
Can't you just set it as the default session?  Then you don't need to change.

---

### Post by zero gravity on 2006-11-30
No can do (gaming prob u know ;) no 3d acc.)
Problem is if I log in with gnome and beryl starts it crashes. Therefore I need it to start only when I log in with xgl.

---

### Post by tomcheng76 on 2006-11-30
Same problem here...
i just made a shoutcut on desktop.
If i login XGL Session. just double click it. otherwise, i dont click it..
a Autostart beryl only with xgl would be great. 
but i dunno how to do it. 
may be we need a script ?

---

### Post by zero gravity on 2006-11-30
I added two scripts when I did my session login with xgl.
The first I put in /usr/bin/startxgl.sh

#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 &&
DISPLAY=:1
exec gnome-session

The other I put in /usr/share/xsessions/xgl.desktop

[Desktop Entry]
Encoding=UFC-8
Name=Xgl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

The second is Just to make the option to start xgl under sessions and it launches script 1.
Script 1 as I understands it starts xgl (the first line) and gnome-session (??).
So my thought was that it would be possible to add beryl-manager in there too.
I "tried" this (just added beryl-manager last thinking it would work like the command line in terminal),  but it didn't seem to work, and I hope this is only because I'm no good at writing scripts (don't know sh*t :( ). 

So my question for the moment is: How can I add beryl-manager to the second script so it starts at the same time??

---

### Post by zero gravity on 2006-12-01
Hm no script guru???

---

