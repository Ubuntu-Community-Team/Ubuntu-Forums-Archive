---
title: "No top panel in GNOME 3 when logged IN"
date: 2011-10-31
forum: Desktop Environments
---

### Post by Ravi5kumar on 2011-10-31
Hi, Hello everybody,

I have very serious problem with GNOME 3. When I log in into Gnome 3 the top panel is vanished. Only a menu bar is displayed as like in the screen shot:(. It ran good previously.I don't how this happened:confused:. I tried to run the command from the terminal 'gnome-shell --replace'. But it gives the following output:

mutter:ERROR:ui/theme.c:1340:meta_color_spec_new_from_string: assertion failed: (spec->data.gtk.state < N_GTK_STATES)
Aborted

Now I have to login into unity :( but I loved Gnome 3. Please help me to fix this problem.:cool:
And yeah I am not running Gnome 3 fallback mode.

System Specification:

Ubuntu 11.10 (oneiric)
Kernal Linux 3.0.0-12-generic
Gnome 3.2.0
CPU : Intel Core 2 Duo 2.20 GHz
4 GB RAM
1 GB Nvidia GT 240 M.

Regards,
Ravi

---

### Post by neigun on 2011-12-08
Hi Ravi

I have the same problem and tried a number of solutions- but no joy. 

Do the windows, if you can open any, have decorations?  The bar shown in your screenshot is the Nautilus bar, a known fault, that I thought had since been resolved.

It might be less than ideal but Gnome fallback is OK if you really don't want to use Unity- at least as a temporary measure until we've resolved this little quirk!

Good luck

Neil

P.S. If you find a solution please post it.

---

### Post by neigun on 2012-01-06
Ravi

Try:

sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user

It worked for me but it will delete your config though.

Neil

---

