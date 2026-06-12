---
title: "OpenBox Wallpaper?"
date: 2008-06-04
forum: Desktop Environments
---

### Post by Protoss on 2008-06-04
So I recently switch to OpenBox, and am loving it...But one thing I've discovered is somehow I always have a wallpaper, even though apparently OpenBox doesn't include this functionality. It shows my regular GNOME wallpaper, but doesn't show the icons like nautilus would. I'm wondering what program could be displaying the wallpaper, any ideas?

---

### Post by urukrama on 2008-06-04
If you haven't changed the default autostart file, Openbox loads gnome-settings-daemon. It controls your fonts, Gtk themes, icons, and wallpaper.

To prevent Openbox from doing so, create a new autostart.sh file (in ~/.config/openbox/) and add only those things you would like to load when Openbox starts. See my Openbox guide for help in setting up an autostart file (link in signature).

The default autostart.sh file is in /etc/xdg/openbox/

---

### Post by Protoss on 2008-06-04
Ahh cool! I followed your guide for some parts, guess I must have passed over the autostart stuff. Thanks for the guide, and the help. I'll try this out.

---

