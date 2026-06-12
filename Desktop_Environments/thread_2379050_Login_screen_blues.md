---
title: "Login screen blues"
date: 2017-11-30
forum: Desktop Environments
---

### Post by nibal on 2017-11-30
Using Ubuntu 14.04.
2 days ago, while uninstalling a program, I accidentally deleted /usr/share/mime/packages.
This caused compiz to segfault at libnux-graphics...
It would prompt me with a weird login screen, all gray with a password textbox, and then it would crash and return me to login again.
Yday i reinstalled shared-mime-info package from a terminal, and got my desktop back.
However my login screen, remained this ugly gray screen.
I've tried everything to change to back, overriding /usr/share/glib2.0/schemas, even tried unity-tweak, to no avail.

1) Where is this ugliness coming from?
2) How can I change it?

TIA
Nikos

---

### Post by nibal on 2017-11-30
Comparing processes under X and under login, they seem to point to:
4 S gdm       4085  4082  0  80   0 - 142304 poll_s 23:45 ?    00:00:00 /usr/bin/gnome-session --autostart /usr/share/gdm/greeter/autostart
1 S gdm       4088     1  0  80   0 -  6111 poll_s 23:45 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session --autostart /usr/share/gdm/greeter/autostart

-> ls /usr/share/gdm/greeter/autostart
orca-autostart.desktop

-> cat orca-autostart.desktop
[Desktop Entry]
Type=Application
Name=Orca screen reader
Exec=orca --disable main-window,splash-window --enable speech,braille
NoDisplay=true
AutostartCondition=GSettings org.gnome.desktop.a11y.applications screen-reader-enabled
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gdm

Certainly seems like this might be the cause, --disable main-window, splash-window, NoDisplay=true,
but substituting gnome-background-panel.desktop for it in the directory, changes nothing:(
At this point I'm at a loss:(

---

### Post by nibal on 2017-12-01
No help here:( 
But searching the web I found the solution. Seems I ended up with a broken gdm:

From a console (<ctrl>-<alt>-F1) type:

sudo dpkg-reconfigure lightdm

and select lightdm from the menu

---

