---
title: "Very small font problem - XMMS, aMule"
date: 2005-01-03
forum: Desktop Environments
---

### Post by thor on 2005-01-03
Hi!

I have a following problem: font used in menus of XMMS and aMule is **very** small, it is almost impossible to be read..  After some search in google I have found that it is somehow connected to GTK, but no solution..

Any hints will be greatly appreciated!

---

### Post by nocturn on 2005-01-03
[QUOTE=thor]Hi!

I have a following problem: font used in menus of XMMS and aMule is **very** small, it is almost impossible to be read..  After some search in google I have found that it is somehow connected to GTK, but no solution..

Any hints will be greatly appreciated![/QUOTE]

The cause is that these are GTK1 apps.
First, find your resolution by typing (in a terminal):
xdpyinfo |grep resol

It should say something like 75x75 or 100X100.

OK, now open synaptic (or use apt), search for fonts.
Locate the font packages for your resoltution and install them.
That fixed it for me.

---

### Post by thor on 2005-01-03
[QUOTE=nocturn]The cause is that these are GTK1 apps.
First, find your resolution by typing (in a terminal):
xdpyinfo |grep resol
[/QUOTE]

It shows:
 resolution:    86x84 dots per inch

What to do now?  :D

---

### Post by nocturn on 2005-01-03
[QUOTE=thor]It shows:
 resolution:    86x84 dots per inch

What to do now?  :D[/QUOTE]

search fonts to be installed (in a terminal):
aptitude update
aptitude search font

There should be entries saying 75 and 100 dpi (don't know the exact names).
Install those.

---

