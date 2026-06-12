---
title: "ubuntu kicks me out"
date: 2008-03-26
forum: Desktop Environments
---

### Post by root_at_home on 2008-03-26
Hi there

I have installed Ubuntu Tweak and made changes, like my Splash screen....

After a reboot I am getting this error when I login.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
SESSION_MANAGER=local/riaanlaptop:/tmp/.ICE-unix/5733

(gnome-session:5733): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Gloss has no size field

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics

(nm-applet:5825): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Gloss has no size field

Initializing gnome-mount extension

(nautilus:5801): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Gloss has no size field


(gnome-panel:5800): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Gloss has no size field


(gnome-power-manager:5822): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.


Can anyone please assist me many thanks
Root_at_home

---

### Post by root_at_home on 2008-03-26
Hi I did some reading and makde a few changes and restarted X now i am getting this error

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
SESSION_MANAGER=local/riaanlaptop:/tmp/.ICE-unix/7502
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics

(gnome-panel:7569): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24


Can anyone help me, 

Thanks
Root_at_home

---

