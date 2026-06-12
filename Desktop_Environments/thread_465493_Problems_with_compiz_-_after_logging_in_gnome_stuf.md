---
title: "Problems with compiz - after logging in gnome stuff fails - black screen, no windows?"
date: 2007-06-05
forum: Desktop Environments
---

### Post by pekkle01 on 2007-06-05
Hi all,

I'm a new upgrader to Feisty Fawn.  I've been on Edgy Eft since November, but haven't really done much playing around with settings, window managers, configurations, etc., so am still new to everything.

Originally I had the default window manager (metacity), then a friend showed me compiz and ran compiz --replace to use compiz as the window manager.   I was looking up how to set that as the default wm (but that's a different story) when I ended up rebooting the machine.  The gdm(?) graphical login screen shows up ok, but when I login, I get an error dialog and then the screen goes black.  Only the mouse cursor is responsive; the keyboard input is not recognized.  At some point the X server killed itself and I was able to login to a virtual terminal.

I restarted X via Ctrl-Alt-Backspace and logged successfully into a Gnome Failsafe session.  Surprisingly compiz is still the chosen / utilized wm.  I was wondering what I should fix to get a regular login session going.

I tried looking around for Gnome-related logs but wasn't sure where to look.

For the record the machine is AMD dual core, nVidia graphics card ... 


Thanks!

---

### Post by burgerboy06 on 2007-09-18
I am having the same problem, i have tried a debug reconfigure but no luck.  I think it may have something to do with a plugin in compiz fusion.  But i do not know how to fix it.

---

