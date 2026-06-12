---
title: "XFCE: Cursor Trouble..."
date: 2008-03-08
forum: Desktop Environments
---

### Post by JordanII on 2008-03-08
I am having trouble with my cursor... no matter what cursor theme I use my cursor changes to default when the cursor is hovering over anything, but firefox and the desktop... when I hover over the panels it changes. What should I do to fix this. The cursor theme I use is awesome, but I want it to work properly.

---

### Post by kerry_s on 2008-03-08
did you log out and back in?

option #2. set it as the default, so it's everywhere.

gksu mousepad /etc/X11/cursors/core.theme

[Icon Theme]
#Inherits=core
Inherits=aero-extra-large

"aero-extra-large" would be the theme name, that just happens to be the 1 i'm using. :)

---

