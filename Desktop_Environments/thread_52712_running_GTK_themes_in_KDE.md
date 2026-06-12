---
title: "running GTK themes in KDE"
date: 2005-07-28
forum: Desktop Environments
---

### Post by kreso on 2005-07-28
I'd like to run the basic GTK themes in my KDE, since now I can see only a flat disguisting theme in my GTK applications.

I don't want to use the QTK-QT-engine application, I just want the basic nice GTK theme.

I found a way to do this: by running /usr/lib/control-center/gnome-settings-daemon
(Oh and yes, I have both KDE and GNOME installed :)

so my question is this: How can I set-up auto running that command when KDE starts, or, if you know of a better way to enable GTK themes.

---

### Post by Mishura on 2005-07-29
When I was running Mepis (A Debian knockoff, that used the Sarge (now Etch) and a bit of Sid), I used a program called "GTK-Theme-Switch", which will load a very tiny program that will allow you to change your GTK themes.  There was one for version GTK1.2 and GTK2.x.

Looks like its in Ubuntu's repositories.  I can't tell if its the one for GTK 1.2 or GTK2.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gtk-theme-switch&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gtk-theme-switch&searchon=name&subword=1&version=all&release=all)

Looking here:  [http://lists.freedesktop.org/archives/xdg/2005-July/007071.html](http://lists.freedesktop.org/archives/xdg/2005-July/007071.html)
It says:  *Currently, kde has the autostart dir in ~/.kde/Autostart*

My best guess is, symlink the executable of the program you want to autorun, and place it there.  I'm not sure, since I don't autostart anything myself.

---

