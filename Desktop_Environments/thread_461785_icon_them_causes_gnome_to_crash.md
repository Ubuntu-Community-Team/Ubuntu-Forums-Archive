---
title: "icon them causes gnome to crash"
date: 2007-06-02
forum: Desktop Environments
---

### Post by Death_Sargent on 2007-06-02
I have been trying to use the OSX icon theme from 

[http://nekohayo.googlepages.com/icons](http://nekohayo.googlepages.com/icons)

however everytime i try to log in with said theme i get a message about my sesion only lasting ten seconds although while on nonxgl sessions everything renders as it should. though I still get this error code in the box

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "pete"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/pete-laptop:/tmp/.ICE-unix/8217
Initializing nautilus-main-menu extension
Initializing gnome-mount extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

** (gsynaptics-init:8311): WARNING **: Using synclient
Xlib: connection to ":0.0" refused by server

Xlib: No protocol specified



(firestarter:8314): Gtk-WARNING **: cannot open display:  
/usr/local/bin/start_beryl.sh: Error: beryl-manager not launched. Xgl not running?
Unknown parameter CoastingSpeedThreshold

(search:8303): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:8315): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:8316): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

---

### Post by Death_Sargent on 2007-06-04
resolved here
[http://ubuntuforums.org/showthread.php?p=2780856#6](http://ubuntuforums.org/showthread.php?p=2780856#6)

---

