---
title: "LXDE startup applications?"
date: 2009-09-26
forum: Desktop Environments
---

### Post by xghstst0riesx on 2009-09-26
I am using the LXDE desktop environment as provided in the standard repos. I would like to have network manager start up by default but I can figure out how. I´ve tried adding the line ¨nm-applet &¨ to ~/.config/openbox/autostart.sh but that didn´t seem to work.

---

### Post by kerry_s on 2009-09-26
[http://wiki.lxde.org/en/LXSession](http://wiki.lxde.org/en/LXSession)

---

### Post by Lukios on 2009-09-26
you can either make a .desktop or you can put what ever you want to start up in the /etc/xdg/lxsession/LXDE/autostart It will look something like this.

@lxde-settings
@xscreensaver -no-splash
@pcmanfm -d
@lxpanel --profile LXDE

just add 

@whatever_you_want_to_startup

.desktop items are in this folder

/etc/xdg/autostart

example

@gnome_panel

to use gnome panel

---

