---
title: "Unable to find provider 'gnome-wm', etc."
date: 2010-06-05
forum: Desktop Environments
---

### Post by Phiwum on 2010-06-05
Hello.

I recently installed Lucid on a new hard drive.  I had a list of installed packages from a previous machine and installed them on the new machine.  Unfortunately, this broke something.  Now, I see the following .xsession errors when I log in (with the gnome wm).

/etc/gdm/Xsession: Beginning session setup...
No default user directories
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[5076]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
gnome-session[5076]: WARNING: Unable to find provider 'gnome-panel' of required component 'panel'
gnome-session[5076]: WARNING: Unable to find provider 'nautilus' of required component 'filemanager'
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.0.

The result is a completely borked windows session.  A beautiful view of the wallpaper, but no functionality that I can find.

I installed *lots* of packages, so it's hard to figure out which one screwed stuff up.  Any help would be appreciated.

---

