---
title: "xubuntu gutsy screensaver trouble"
date: 2007-10-25
forum: Desktop Environments
---

### Post by dgraham on 2007-10-25
Hey everybody, I just did a clean install of Gutsy, and have run into a screensaver problem. Xubuntu now comes with gnome-screensaver instead of xscreensaver. It was easy enough to install one and remove the other to get it back like I wanted, but the xscreensaver package doesn't seem to take care of business anymore.

gnome-screensaver was run when I logged in automatically, but xscreensaver does not, I had to add an autostart entry for it. The Screensaver button disappeared from the Settings Manager, and Screensaver Settings now reports 'Xfce Settings Manager error: No such plugin "screensaver"' instead of doing anything useful. This forces me to Alt+F2 xscreensaver-demo, which is very annoying.

Anyone know how to tell Xfce that xscreensaver really is installed? It has always worked perfectly for me since Dapper...

---

### Post by dgraham on 2007-10-26
Well, I got it working with some ugly hax. Please post if you know how to fix it properly!

[LIST]
[*]install xscreensaver (the purpose of this should be obvious).
[*]install gnome-screensaver. (icons in the settings menu and Settings Manager now work)
[*]create an Autostart entry with xscreensaver -no-splash in it. (runs xscreensaver at login)
[*]sudo killall gnome-screensaver (kills gnome-screensaver)
[*]sudo chmod -x /usr/bin/gnome-screensaver ("disables" gnome-screensaver while keeping dpkg happy)
[*]sudo chmod -x /usr/bin/gnome-screensaver-command (ditto)
[*]sudo cp /usr/bin/xscreensaver-demo /usr/bin/gnome-screensaver-preferences (Xfce screensaver settings icons now run xscreensaver-demo instead of gnome-screensaver-preferences)
[/LIST]

---

### Post by Carl Foxmarten on 2007-11-19
Hey, thanks for posting at least this amount of information.

I just updated my laptop to Gutsy hoping that the nvidia GLX driver would work properly for my graphics card (it didn't, I may need to look into another distro to get it to work :( ), but I found that the lovely Xscreensaver package got superseded by the *extremely* dumbed-down Gnome-Screensaver package (I prefer to choose what screensavers I run, as not all of them actually work on my system due to the above problem, nor do I like many of them).

I'm hoping that somebody comes along to let us know how the compatibility between the two packages will turn out, as I'm definitely *not* happy with Gnome's version.

---

### Post by landry on 2008-01-17
check out this link on these forums for a complete description of how to swap out gnome-screensaver and swap in xscreensaver:

     [http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

---

