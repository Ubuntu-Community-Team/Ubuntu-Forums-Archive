---
title: "[SOLVED] Help direly needed for XFCE"
date: 2008-11-15
forum: Desktop Environments
---

### Post by djbushido on 2008-11-15
Ok, so this may sound weird.
I am using xubuntu, and am writing this from GNOME, had the idea to install an alternate desktop.
I don't know how this happened, but this morning when I started XFCE, it loaded the desktop manager, and then froze. I am using the Balou splash screen on startup, so this is how I knew that the desktop manager froze. I tried reinstalling the xfce packages via synaptic on GNOME, but that did nothing, and I am running into the same problem. I don't know how to provide more information, and would appreciate any and all help. Thank you.

EDIT: Ok, so I think the problem is the splash screen, because xfce loaded fine on a different user. Does anybody know how to change the splash screen and/or display engine from a GNOME session?

---

### Post by djbushido on 2008-11-15
Turns out that the balou splash screen was the problem. Changing the config file in ~/.config to read no splash screen turned out to be the solution. Thanks to all who thought about helping.

---

### Post by timjohn7 on 2008-11-16
I've got the opposite of your problem... my Gnome desktop has disappeared... I have my background picture and no functionality... no Panels, no alt F2, no left or right click.  The only thing I can do is select other desktops with ctrl alt left or right.  Its as if the background photo is in front of everything else.  So I'm writing this from XFCE.  I have tried creating another user but the problem is the same.
I'll try your solution to your problem to solve mine.
And I enjoy your thanks! :grin:

---

### Post by djbushido on 2008-12-04
Been thinking on this for a while, make sure gdm is up and running, try re-installing gnome, because it sounds like just X11 is running.

---

