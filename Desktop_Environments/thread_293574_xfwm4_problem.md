---
title: "xfwm4 problem"
date: 2006-11-05
forum: Desktop Environments
---

### Post by stmacchiavelli on 2006-11-05
Hi every body,

i'm using xubuntu and have the following problem with graphical session:

when i log in into xubuntu all the windows appear without borders and resize/minimize icons. I have to run 

sudo xfwm4

in a shell to restore the normal windows apparence but it works only until netx reboot.

This is the xsession.error file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "stefano"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

(xfdesktop:4910): Gtk-WARNING **: Theme file for default has no name


(xfce4-panel:4916): Gtk-WARNING **: Theme file for default has no name


(xfce4-menu-plugin:4919): Gtk-WARNING **: Theme file for default has no name


(Terminal:4948): Gtk-WARNING **: Theme file for default has no name


(xfce4-session:4904): Gtk-WARNING **: Theme file for default has no name


(xfce-mcs-manager:4908): Gtk-WARNING **: Theme file for default has no name


(Gecko:4970): Gtk-WARNING **: Theme file for default has no name


(Thunar:4921): Gtk-WARNING **: Theme file for default has no name

method return sender=:1.0 -> dest=:1.2
method return sender=:1.0 -> dest=:1.3


It looks like gnome and xfwm4 starts together...and no thene is found by xfce..

I don't know what to do...any idea ??

---

### Post by tvcrabo on 2008-02-26
I have just the same problem... the only difference is that i use the command 

xfwm4 --replace

But when i restart i have to do it again caus it wont start.

Can anyone help?

---

