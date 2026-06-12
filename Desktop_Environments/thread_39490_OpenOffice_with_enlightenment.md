---
title: "OpenOffice with enlightenment"
date: 2005-06-05
forum: Desktop Environments
---

### Post by LichiMan on 2005-06-05
Hi all,
I don't know why but when I run ooffice or ooffice2 in enlightenment, it doesn't load the gtk2 version, but when i run it under a gnome session, it does.
When I load a enlightenment session, I load gnome-settings-daemon in its startup, so I get the gtk theme in my gtk applications, etc...
What I need to do to run the gtk2 version of openoffice into enlightenment?
Thanks!

Miguel.

---

### Post by Joeb on 2005-06-05
Evidently, Openoffice only uses gtk2 if it detects that gnome itself is running.  I'm not sure of the detection process it uses (ie what component(s) need to be running).  I did find the following on the internet:

[I]You can override the detection by uncommenting the line in
/etc/openoffice/openoffice.conf:

# force OOo to use theme settings from gnome or KDE or disable?
# set to 'gnome', 'kde' or 'none' to override the autodetection
#export OOO_FORCE_DESKTOP=gnome[/I]


Joeb

---

### Post by LichiMan on 2005-06-05
Thank you so much!
It worked for openoffice 1.3.
For openoffice 1.9 I've seen that there's an /etc/openoffice2 file and I've edited it but for openoffice 1.9 doen't work doing the same thing than for openoffice 1.3
Thanks again!

---

