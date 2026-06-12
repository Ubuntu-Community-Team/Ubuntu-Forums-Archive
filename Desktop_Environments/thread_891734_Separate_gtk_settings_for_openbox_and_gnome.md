---
title: "Separate gtk settings for openbox and gnome?"
date: 2008-08-16
forum: Desktop Environments
---

### Post by cchung85 on 2008-08-16
Is there a way to have separate Gtk settings for say Openbox and Gnome?
I toyed around with openbox last week but the theme settings in it messed up ubuntu settings and fonts.

Ideally I'd like to be able to have separate profiles so that they can be different looks.

I found this:
[http://urukrama.wordpress.com/2008/05/21/using-different-gtk-settings-in-different-sessions/](http://urukrama.wordpress.com/2008/05/21/using-different-gtk-settings-in-different-sessions/)

But it says it's for PekWM and also it seems a bit complicated, I was wondering if anyone had an easier solution.

Thanks

---

### Post by spupy on 2008-08-16
In GNOME you have the gnome-settings-daemon that is taking care of themes, fonts, etc.
In you Openbox session this program is probably not running. In this case you can have your settings in a gtkrc file. The name of this file is ".gtkrc-2.0" and it is located in your home directory. (The name starts with "." so it is a hidden file). My gtkrc file looks like this:
```
gtk-theme-name="Murrina Deviant2"
gtk-icon-theme-name="Tango"
gtk-font-name="Sans 9"
```
The values here are self-explanatory, I hope. In openbox gtk settings will be read from that file; in GNOME the daemon will take care.
(I'm not 100% sure that the settings-daemon takes precedence over the gtkrc file, but try it anyway.)

---

### Post by cchung85 on 2008-08-16
Thanks, I will give that a try tonight. I feel like setting up open box again (just got rid of vista for good).

---

