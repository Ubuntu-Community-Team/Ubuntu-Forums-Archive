---
title: "Gnome panel oddity"
date: 2011-05-20
forum: Desktop Environments
---

### Post by philipg on 2011-05-20
interesting glitch observed in gnome panel 2.30.2 under ubuntu lucid 64.
my gnome panel runs vertically up the lefthand side of my widescreen monitor (makes a lot more sense that wasting the space at the bottom/top of the screen space on a widesreen aspect ratio). notification & indicator applets are both running on this panel next to each other. 

when starting guayadeque music player its tray icon (ie notification applet area) would only appear as a thin sliver instead of a full icon. going into guayadeques preferences and reseting to no-tray-icon then back to yes-tray-icon would cause the full icon to appear.

If I change the properties of both notification & indicator applets to be NOT-locked-to-panel then guayadeque will start with a full icon as normal. If I lock-to-panel either or both notification & indicator applets then the guayadeque tray icon returns to its buggy  behaviour.

Haven't noticed any other systray programs behaving this way yet.

---

### Post by Copper Bezel on 2011-05-21
Weird - so locking or being next to a locked panel object is causing the Notification Area not to expand for that one app. Thanks for sharing the tip - someone else might run into the same problem.

---

### Post by ivanovnegro on 2011-05-25
Its a known issue with Guayadeque and maybe also with GMusicbrowser on Lucid and Maverick, I think its solved under Natty.
I think it was a mix of a bug of the icon and the panel, I forgot it.
Still the icon of Guayadeque is a bit poor on Natty and I even saw a glitch once but not as bad like before.

---

