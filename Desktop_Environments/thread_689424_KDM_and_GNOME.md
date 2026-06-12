---
title: "KDM and GNOME"
date: 2008-02-06
forum: Desktop Environments
---

### Post by tim71 on 2008-02-06
I have been using KDM as display manager for a long time and had no problem with any of desktop environments I am using - that's KDE, GNOME and XFCE.

But some time ago strange thing happened - KDE and XFCE are fine, but if I try to login in GNOME session, then everything seems to be broken - icons are missing and changing icon themes does not have any effect. Main menu on the panel is also broken as many items are missing from it. Even worse - some GNOME applications don't work, although they work in KDE or XFCE session.

Here's a little example -  
```
~$ gnome-system-monitor

(gnome-system-monitor:9794): Gtk-WARNING **: Could not find the icon 'lpi-help'. The 'hicolor' theme
was not found either, perhaps you need to install it.
You can get a copy from:
        http://icon-theme.freedesktop.org/releases

** (gnome-system-monitor:9794): CRITICAL **: failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme

(gnome-system-monitor:9794): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (gnome-system-monitor:9794): CRITICAL **: failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme

(gnome-system-monitor:9794): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (gnome-system-monitor:9794): CRITICAL **: failed to load icon 'lpi-bug': Icon 'lpi-help' not present in theme

** (gnome-system-monitor:9794): WARNING **: SELinux was found but is not enabled.

Segmentation fault

```
Looks like problem with gnome-hicolor theme - which is installed...

Initially I thought, that this might be caused from experimenting with X forwarding and running gnome-session on a remote machine simoultaneously with a local XFCE session - because GNOME looked absolutely fine on the remote machine.

Now I tried other trick - I changed default-display-manager to gdm and guess what? I logged in to GNOME session, and everything was OK.

Then I changed default-display-manager back to kdm and tried to log in to GNOME session and everything was broken again.

What might be causing this problem? Everything was fine before and logging into GNOME session from kdm caused no problem at all. I have some reasons to use kdm instead of gdm and not interested in changing that.

Any ideas? :confused:

---

### Post by tim71 on 2008-02-10
Here is the screenshot to illustrate the problem

---

### Post by tim71 on 2008-02-12
This is the wiew from icon theme selection window...

I also noticed one worse thing -GNOME cannot open any application by clicking a .desktop file.


Also tried this thing here => [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/") without any effect.

---

### Post by tim71 on 2008-05-07
Have to bump this thread one more time....

I was hoping that upgrades will solve this thing but no - I still can launch gnome-panel in xfce4 session and it works OK, but in GNOME session menus are almost empty and even 'Quit' command does not work - actually nothing happens after that and only way to end the session is killing X.

I am at loss here because even simplest things will not work in GNOME session although everything is fine in KDE3 or xfce4 session - even with GNOME applications...

:confused:

---

