---
title: "Missing most of the upper panel in GNOME Classic"
date: 2013-04-06
forum: Desktop Environments
---

### Post by andrei77 on 2013-04-06
When I log into Gnome Classic (Ubuntu 12.04), my upper panel has missed all applets and shortcuts, except two dropout menus in the left - Applications and Places. I even can't log out - I have to do it by killing gnome-session via tty0. I re-installed gnome-panel but it gave no result, so there's some other application that has to be renewed, but I can't guess which. Any help is much welcome.

---

### Post by ibjsb4 on 2013-04-06
Can you just rebuild the panel?

Alt + right click > add to panel

---

### Post by andrei77 on 2013-04-06
I can't do it by Alt + right click, but it works with Alt + Win Key. Yes, the appears a pop menu with Add to panel, I tried to add "Shutdown" applet, but after that the panel lost all of its contents. Thinking it was a new panel I deleted it, after what both top and bottom panels disappeared. If this continues like this, I'll need just to re-install GNOME at all.

---

### Post by ibjsb4 on 2013-04-06
```
sudo apt-get install --reinstall gnome-panel
```

Have you tried that?

---

### Post by andrei77 on 2013-04-06
Yes of course, that was the first thing I did. I re-installed all the main GNOME packages and deleted folder ~/.gconf, but nothing changed. What makes it even more ridiculous, sometimes when I log in I get the missing right part of the panel (with time, weather and shutdown facility) in the left corner where the programs menu is supposed to be! So I log out and in again, and then it returns to the existing state.

Yesterday I was compiling packages for Wayland (according to these instructions: [http://wayland.freedesktop.org/building.html](http://wayland.freedesktop.org/building.html)) and adding lots of dependent packages, may be I installed something that conflicts with Gnome? I remember it started after I compiled Weston. First all I got was both top and bottom panels at the top of the screen (with no applets or anything), then when I re-installed gnome-panel it started to be like I said in my first post - Applications, Places and that's all. Really weird.

I'm using the latest versions of gnome in Ubuntu repositories: gnome-shell-3.4.1-0ubuntu, gnome-session-3.2.1-0ubuntu8, gnome-panel-1:3.4.1-0ubuntu1.1 .

---

