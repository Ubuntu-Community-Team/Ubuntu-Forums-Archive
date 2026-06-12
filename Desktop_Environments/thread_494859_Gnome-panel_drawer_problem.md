---
title: "Gnome-panel drawer problem"
date: 2007-07-07
forum: Desktop Environments
---

### Post by ftmichael on 2007-07-07
I added a drawer to my top panel, which I love, but when I click it, instead of the drawer appearing directly below the icon, it appears all the way over on the left side of my screen, in the top left corner - the first icon in the drawer actually covers the Ubuntu icon that's on the Applications menu.  What's that about, and can I fix it?

(Interestingly, after X starts, the drawer opens where it should the first time I click it; every time after that, until I restart X, it's over in the top left corner.)

Michael

---

### Post by ftmichael on 2007-07-15
Bump.

---

### Post by wallneradam on 2007-08-15
I had the same very annoying problem some times ago. I think it's a bug in the drawer applet. The problem occurs when you switch off the panel animations, or simply the drawers' animation (it was a long time to discover this :) )

You can check it with gconf-editor. You need to switch on enable_animations flag at /apps/panel/toplevels/panel_0, /apps/panel/toplevels/panel_1...
If it doesn't help, you may globaly switched off the animations. You can search keys with gconf-editor contain "anim".

I hope it will help.

Adam

---

### Post by ftmichael on 2007-10-15
enable_animations is already checked in /apps/panel/toplevels/top_panel_screen0.  Should enable_buttons be checked also?  It isn't currently.

There is no enable_animations in /apps/panel/toplevels/panel_0, but the drawer is on the top panel, so I assume that's appropriate.

I searched for 'anim' and found a bunch of stuff; the appropriate-looking ones that I looked at all already had enable_animations checked.

Michael

---

### Post by ftmichael on 2007-12-02
Bump.  Problem still not resolved.

Michael

---

### Post by atrus on 2008-02-16
Likewise. I'd love to know what's going on here.

---

