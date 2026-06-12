---
title: "gnome-dock launchers and icons"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by jfca283 on 2007-05-11
hi
i use dapper and i achieved installing gnome-dock
i followed this tutorial
[http://ubunteros.wordpress.com/2006/08/10/gnome-dock-le-dock-merveilleux/](http://ubunteros.wordpress.com/2006/08/10/gnome-dock-le-dock-merveilleux/)
and it worked great
but i don't know how to aggregate launchers
the icons must be in the folder cairo-dock with the SVG extension, right?
i edited the cairo-dock.c file
but it didn't apply to the dock
e.g. i erease the line
{"im.png", "IM", "gaim"}, for
{"im.png", "IM", "pidgin"},
but pidgin doesn't start
in console, i write pidgin and it runs
i don't know what i did wrong
can you help me?
thanks

---

### Post by nuahs on 2007-05-11
Every time you change the cairo-dock.c file you need to 'cd' to the cairo-dock folder and 'make' again. Then run and you should see the changes. Kind of a pain in the a** :D

---

### Post by searayman on 2007-05-11
dude just try awn dock... check in my signiture below for a link.

---

### Post by jfca283 on 2007-05-11
i've investigated about awn, but on dapper nothing...
and i'm not interested in making an upgrade, losing my configuration files and so on...

---

