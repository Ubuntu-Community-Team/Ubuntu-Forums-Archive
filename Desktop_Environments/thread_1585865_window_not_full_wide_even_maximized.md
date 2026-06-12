---
title: "window not full wide even maximized"
date: 2010-10-01
forum: Desktop Environments
---

### Post by rajeshjsl on 2010-10-01
see this even the window is maximisez its not fully wide 

the window was fine before and after compiz installation .
but after installing some other apps this happend , how to fix it ?

see this image

[[IMG]http://img199.imageshack.us/img199/696/screenshotipl.png[/IMG]](http://img199.imageshack.us/i/screenshotipl.png/)

---

### Post by roggenschrotbrot on 2010-10-01
from the looks of it gnome-panel might have reserved this area, i'd suggest to check /apps/panel/toplevels in gconf-editor. if there are multiple entries check if ones orientation is set to "left". if so, change it to anything else to see if you gap disappears/moves.

---

