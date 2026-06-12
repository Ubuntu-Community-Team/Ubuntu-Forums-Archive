---
title: "HPLIP on startup annoying"
date: 2009-01-04
forum: General Help
---

### Post by kwilliam on 2009-01-04
I plugged in an HP printer to my laptop and installed it, and now every time I boot the HPLIP Status Servus program comes up with an icon in the system tray, and gives an error message about how it can't find the printer (because it's not plugged in). How do I stop HPLIP from running every start up?

---

### Post by rbmorse on 2009-01-04
Go to 

system > preferences > sessions  

and remove the check from the box next to "HP System Tray Service"

---

### Post by kwilliam on 2009-01-04
> **rbmorse said:**
> Go to 

system > preferences > sessions  

and remove the check from the box next to "HP System Tray Service"

That sounds like Gnome directions. I'm in Kubuntu here, and there appears to be no GUI. I solved the problem by finding all the autostart directories  with "locate autostart". It appears autostart programs are controlled with .desktop files now, in several directories. All the KDE programs were in /usr/share/autostart, but the HP printer program was in /etc/xdg/autostart along with some Ubuntu specific programs. Deleting /etc/xdg/autostart/hplip-systray.desktop made it quit starting on log in.

---

### Post by rbmorse on 2009-01-04
> **kwilliam said:**
> That sounds like Gnome directions. I'm in Kubuntu here

Glad you got it working. I missed the flag on your OP.

---

