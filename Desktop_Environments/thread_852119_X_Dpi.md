---
title: "X Dpi"
date: 2008-07-07
forum: Desktop Environments
---

### Post by vilon on 2008-07-07
Hi.

When I start a GNOME session with my user, the X dpi setting is 96 (according to xdpyinfo output). I'm not talking about the GNOME font DPI setting, but the X one. I can change it to the correct setting (116) with xrandr --dpi 116.

The interesting thing is that if I start X from the command line (xinit) or start a GNOME session with another user, the DPI value is 116. The screen dimensions are properly declared in /etc/X11/xorg.conf, and also parsed correctly - according to /var/log/Xorg.0.log the DPI value is set to 116 when the server starts.

So X starts up alright with the correct values, and sometime during the start of the session DPI is set to 96. Now, I can't remember having made any changes that would cause this ridiculous behaviour, but since it seems to be somewhere in my users settings I have to presume I somehow did.

Now I ask if someone would kindly tell me where to look for it, because I have looked everywhere I can think of and found nothing. I admit that is not a lot of places, but it includes the GDM conf files, GNOME session and other obvious ones. Help is appreciated, since right now all I can think of is doing xrandr --dpi 116 every time I log on or creating a new user with all the work of setting things up properly.

---

### Post by vilon on 2008-07-08
I believe I have found the culprit. After I create a new user account, everything works just fine until I start gnome-display-properties. If I start, click Detect displays and click Apply, DPI will be set to 96 right away and every time that user logs in.

I'm going to create a bug report about this. I'd still be very grateful for any hints about how get the behaviour back to normal.

---

### Post by vilon on 2008-07-08
I found it. In case anyone else gets hit by the same bug: removing ~/.gnome2/monitors.xml will do the trick.

---

