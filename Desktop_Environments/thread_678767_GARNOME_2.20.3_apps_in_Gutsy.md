---
title: "GARNOME 2.20.3 apps in Gutsy"
date: 2008-01-26
forum: Desktop Environments
---

### Post by kjetilho on 2008-01-26
Thought I'd put a message here with my notes on how to get GARNOME 2.20.3 running.  This is just a supplement to the information in the README.

First of all, install all prerequisites.  Unfortunately, the list in the README isn't quite accurate, some of the names are wrong, but I put my corrected list in /tmp...  You'll figure it out, mosly change -devel to -dev.  One gotcha for me was that the "docbook" is not listed, and is not pulled in by dependencies even if you have 9 other docbook related packages installed.

Since I run Ubuntu's KDE, I'm not interested in running a new GNOME session, I only want the new versions of Evolution, Gnumeric etc.  This means I should keep my system daemons running (hald, dbus etc), they seem to be compatible, anyway.
To accomplish this, make $GARNOME/var/lib/dbus/machine-id a symlink to /var/lib/dbus/machine-id (GARNOME being the directory where you installed it, I chose /opt/garnome-2.20.3).  One daemon needs to be replaced, though.  Without the correct gnome-settings-daemon, e.g., icons will go missing.
```

pkill -f gnome-settings-daemon
$GARNOME/libexec/gnome-settings-daemon &
```

Another problem is that GARNOME ships with unpatched libxml2 2.6.30, which makes the file chooser dialog etc. crash.  This has been fixed in the Ubuntu version of the package, so I simply replaced $GARNOME/lib/libxml2.so.2.6.30 with a symlink to /usr/lib/libxml2.so.2.6.30

To make it easier to launch the GARNOME installed version of the applications, I made a simple wrapper script ~/bin/garnome which looks like this:
```

#! /bin/sh

GARNOME=/opt/garnome-2.20.3

PYTHONPATH=$GARNOME/lib/python2.4/site-packages:$GARNOME/lib/python2.4/site-packages/gtk-2.0
GDK_USE_XFT=1
XDG_DATA_DIRS=$GARNOME/share
XDG_CONFIG_DIRS=$GARNOME/etc/xdg
MANPATH=$GARNOME/man:${MANPATH-/usr/share/man}
PATH=$GARNOME/bin:$PATH

export PYTHONPATH GDK_USE_XFT XDG_DATA_DIRS XDG_CONFIG_DIRS MANPATH PATH

"$@"
```

Now I can write "garnome evolution" or even "garnome man gconftool-2" to get the right version, and keep the normal Ubuntu software completely unchanged.

PS. the garnome build stops with GDM here (undefined reference to gdm_debug), but since the apps I'm interested in compiled cleanly, I haven't looked into it.

---

