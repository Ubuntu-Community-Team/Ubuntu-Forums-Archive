---
title: "Fluxbox wont run with GDM"
date: 2007-05-06
forum: Desktop Environments
---

### Post by Hatty on 2007-05-06
I have fluxbox installed from the repos. When I try to run fluxbox (from Fluxbox session or XClients script (both .Xclients and .xsession have "exec startfluxbox")) GDM gives me a "session lasted less than 10 seconds" error. When I view my .xsession-errors, this is all there is:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "hatty"
/etc/gdm/Xsession: Beginning session setup...
```

What am I to do?

---

### Post by BOBSONATOR on 2007-05-13
im getting the same exact thing.

---

### Post by kerry_s on 2007-05-13
I don't have a .xsession or .xclients in my fluxbox install. you just select fluxbox in the gdm session manger. fuxbox is started with /.fluxbox/startup it looks something  like this->

# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/user/pictures/wallpaper.png
#
# This sets a black background

#/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/user/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor 
#
# Change your keymap:
# xmodmap "/home/user/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

exec wmdrawer &
exec sudo conky &
exec play /home/user/.sounds/startup_1.ogg &
exec xset s off off dpms 0 0 300 &
exec rm ~/.xsession-errors &
exec xrdb -merge $HOME/.Xdefaults &
exec fbpager -w &
exec update-menus &
exec pidgin &


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox 
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/user/.fluxbox/log"

---

### Post by RedSquirrel on 2007-05-13
The important thing about using the ~/.fluxbox/startup file is that
```
exec /usr/bin/fluxbox
```must be the last line in the file. 

Use 

```
exec /usr/bin/fluxbox -log "~/.fluxbox/log"
```if you want logging.

---

