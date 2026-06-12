---
title: "layout switcher in xfce4"
date: 2012-02-19
forum: Desktop Environments
---

### Post by oldnik on 2012-02-19
[no comments] - everything on screenshot
restarting doesn't make sense

---

### Post by ajgreeny on 2012-02-19
That depends on whether or not you need that applet I would think.  Do you need to change your keyboard layout much (it's something I never do), but if not, remove the applet.  If you do really need it, there must be some problem that needs sorting out so that it does not keep crashing.

---

### Post by oldnik on 2012-02-19
Well, usually i use 
> setxkbmap -layout us,it -options ...
to change layout. But the bug is in dropping to default settings after logon from sleep. And sometimes this applet crashes.

---

### Post by LewisTM on 2012-02-19
This applet has had its share of bugs.
The best way to make is run safely is to set everything to default outside of the plugin itself, that means system default settings in the xfce4-settings-manager and of course no setxkbmap command.
Otherwise it will crash.
Or remove it from your panel and go with setxkbmap commands only.

Cheers!

---

### Post by oldnik on 2012-02-19
> **LewisTM said:**
> This applet has had its share of bugs.
The best way to make is run safely is to set everything to default outside of the plugin itself, that means system default settings in the xfce4-settings-manager and of course no setxkbmap command.
Otherwise it will crash.
Or remove it from your panel and go with setxkbmap commands only.

Cheers!

Thank you, LewisTM ! Yes, i'll try it other way i use now. Once you helped me with àccént&#351;. This is second one) 2-0

---

### Post by oldnik on 2012-10-24
To those, who are interested:
now i use quite simple, no-plugins method. Create ~/setxkb.sh with ```
setxkbmap -layout us,de,fr -option grp:lwin_toggle,compose:ralt
``` and add this script to autorun.
Have fun with linux! :)

---

