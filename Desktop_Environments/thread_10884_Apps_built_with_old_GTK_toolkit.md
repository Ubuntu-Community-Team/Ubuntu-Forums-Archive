---
title: "Apps built with old GTK toolkit"
date: 2005-01-12
forum: Desktop Environments
---

### Post by X-fact0r on 2005-01-12
Hi,
is there any way of making apps that were built with older GTK toolkit look nicer under Gnome?
i.e. XQF ([www.linuxgames.com/xqf/](www.linuxgames.com/xqf/))

Whenever I run such apps I get a very big font and the window control doesn't match the one currently in use via Themes app.  :-( 

Using Warty with standard kernel, just with all upgrades from the stable/unstable/universe branches.

Thanks in advance.

---

### Post by minio on 2005-01-12
yes there is  :) You need to find and install gtk version of your gtk2 theme. Gtk applications follow the theme you have selected via Theme app if there is version for gtk installed.  I think that fonts can be changed only by editing files. You should look into file gtkrc, but i am currently on windows machine so im not sure where to find it (the one containing your personal settings maybe in ~/.gtk/ and files with global settings in /etc/gtk). And sorry for my english :)

---

### Post by ulrich on 2005-01-12
and specific to xqf:
or go to [http://packages.debian.org/testing/games/xqf](http://packages.debian.org/testing/games/xqf) and download the package.
install it via 'dpkg -i xqf...blah.deb'
works without pain here and is compiled against gtk2 :)

if it complains about other packages needed: just get them from the same site.

hth

ulrich

---

### Post by X-fact0r on 2005-01-17
Thanks for the help, that really worked out!  :grin: 
Any similar solution/procedure for xmms?

---

### Post by ilari on 2005-01-17
[QUOTE=X-fact0r]Thanks for the help, that really worked out!  :grin: 
Any similar solution/procedure for xmms?[/QUOTE]
 Try BMP (Beep Media Player), which is a GTK+2-fork of XMMS.

From Synaptic package manager:
BMP is "Versatile X audio player that looks like Winamp
Beep Media Player is a player for various audio formats,
with a customizable interface based on GTK2."

---

### Post by valadil on 2005-01-17
Download some gtk1 themes and grab gtk-theme-switch from apt.  It includes two programs, switch and switch2.  They let you change your gtk1 and gtk2 themes.  One of the first things I do when I get a new install is apt-get install gtk-theme-switch gtk2-engines* gtk-engines*.

---

