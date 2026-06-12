---
title: "Kubuntu Nearly Blank Screen"
date: 2009-03-29
forum: General Help
---

### Post by AC-BC on 2009-03-29
Today I booted up, logged on at the KDM Login Screen, the KDE plaque came up, the first icon started to rez, and then the screen went completely white.  After a while it went completely black.  And then the mouse appeared, and then the SHADOWS of some windows.

I could not see the windows or any of their content, but only the shadows of about 3 (a pail blue on black).  With a little care, I could estimate where the title bar was, click and drag it around, and the associated shadow would also move around.  Apparently, my desktop is there, but not properly visible.

I've been running Kubuntu for a couple of weeks now, and this has never happened before.

I tried getting out of X and restarting it (Ctrl-Alt-Bksp), but it did the same thing.

I switched to a terminal (Ctrl-Alt-F1), and logged on.  The terminal worked fine.

I then tried creating a second GUI terminal (startx -- :1 &).  That too worked, giving me a GNOME interface at Ctrl-Alt-F9.

I have an nVidia 8800 GTS graphics card.

Anybody have any clues as to what happened and how to fix this?

---

### Post by AC-BC on 2009-04-23
OK, I think I have an idea what the problem is, but I still need some help testing it.

I think it is an incompatibility with display settings.  I need to be able to reset the KDE display back to default.  Can anyone PLEASE tell me how to do that?  (Obviously, or not, it needs to be done in another window manager or at the CLI.)

AC-BC

---

### Post by AC-BC on 2009-04-24
Never mind.  I found the solution on another forum.

Thanks.

OH!  The solution!  It was just a matter of deleting the ~/.kde directory.  KDE then rebuilds it to defaults upon relog.

---

