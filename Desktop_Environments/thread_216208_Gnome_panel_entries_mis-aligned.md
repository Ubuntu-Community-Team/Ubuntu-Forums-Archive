---
title: "Gnome panel entries mis-aligned"
date: 2006-07-15
forum: Desktop Environments
---

### Post by robbbert on 2006-07-15
Hi, this is about the upper Gnome panel. Normally, there is a defined sequence (from left to right) in it:

1. Menu entries ("Application", "Places", "System")
2. Predefined and custom application launchers
3. Predefined applets (like "Weather" and "Show Desktop")
4. Tray applications (like "Software Updates")
5. Clock
6. Quit button

That sequence has changed for my panel. Currently, everything is aligned right; the sequence (from left to right) is:

1. Predefined and custom application launchers
2. Predefined applets (like "Weather" and "Show Desktop")
3. Menu entries ("Application", "Places", "System")
4. Clock
5. Tray applications (like "Software Updates")
6. Quit button

Diagnosis: I had  some troubles with user settings before (first, /etc/passwd was lost, and when being restored, there were no Read permissions on it for some time). 
I'd also changed the screen resolution temporarily, at that time.
Under ~/.gconfd and ~/.gconf I can't seem to find any config file being related to gnome-panel. 
Also, /etc/X11/xorg.conf hasn't been touched since the misbehaviour occured.

Could you please tell me where to re-configure the Gnome panel?

Thanks

---

### Post by bulldog on 2006-07-15
You could simply right-click your mouse and move the items to your liking.
You could even pin them down at that place if you want.
If there is a config file where you could figure things out, I don't know,I've never search for it.

---

### Post by robbbert on 2006-07-15
Oops! That was easy... Thank you!

---

