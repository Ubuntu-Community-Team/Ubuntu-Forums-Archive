---
title: "GNOME loading issues &amp; screen res..."
date: 2005-07-27
forum: Desktop Environments
---

### Post by jaspeers on 2005-07-27
Two questions:

1) If I reboot my system - not just logging out of Gnome but an actual reboot - the gnome panel can take up to twenty minutes to load.  Sometimes if I reset the X server and log in again, it'll pop right up.  Sometimes not.  Sometimes the bottom panel - window list / show desktop button only - will partially load.  The top panel pretty much never loads immediately.  I also noticed the Alt-F2 run program shortcut doesn't work until the panels load... can anyone give me a hint so I can try and figure out why this is happening and fix it?  It's extremely obnoxious right now...

2) I tell Ubuntu to remember my screen resolution (1600x1200) through the preferences / screen resolution settings, but it always goes back to 1152x864 anyway, which looks awful.  GDM seems to be set to 1600x1200, though I have no way of knowing for sure.  There's definitely a switch once I log onto gnome... Any way to make gnome go to 1600x1200 every time?

---

### Post by heimo on 2005-07-27
[QUOTE=jaspeers]Two questions:
2) I tell Ubuntu to remember my screen resolution (1600x1200) through the preferences / screen resolution settings, but it always goes back to 1152x864 anyway, which looks awful. GDM seems to be set to 1600x1200, though I have no way of knowing for sure. There's definitely a switch once I log onto gnome... Any way to make gnome go to 1600x1200 every time?[/QUOTE]

Easy way is to edit /etc/X11/xorg.conf
 ```
sudo gedit /etc/X11/xorg.conf
``` 
locate the lines with resolutions and remove all but 1600x1200 - of course then you will only have that one and it's possible that for example fullscreen games can't use other resolutions (I'm not sure about that). Also just changing the order in which resolutions are listed can help.

---

### Post by Joeb on 2005-07-27
[QUOTE=jaspeers]Two questions:

1) If I reboot my system - not just logging out of Gnome but an actual reboot - the gnome panel can take up to twenty minutes to load.  Sometimes if I reset the X server and log in again, it'll pop right up.  Sometimes not.  Sometimes the bottom panel - window list / show desktop button only - will partially load.  The top panel pretty much never loads immediately.  I also noticed the Alt-F2 run program shortcut doesn't work until the panels load... can anyone give me a hint so I can try and figure out why this is happening and fix it?  It's extremely obnoxious right now...
[/QUOTE]

Look in the .gnome2 directory in your home directory and delete the session file located there and see if that fixes the problem.  

Joeb

---

