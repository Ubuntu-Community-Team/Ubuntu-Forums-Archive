---
title: "Nautilus always opens an extra directory"
date: 2010-05-22
forum: Desktop Environments
---

### Post by andrewkirk on 2010-05-22
When I open a directory from the Places menu on the Gnome panel, two Nautilus windows open up. One is the location I asked for. The other is always "/media/Data/ZZZMaint/PC/R stats pkg". I think it may be to do with the fact that some time earlier I had created a launcher in the Main Menu - called "R documentation"', with command "nautilus --no-desktop '/media/Data/ZZZMaint/PC/R stats pkg' " (the idea was to have a menu item that opened up a folder containing a set of documents I refer to). I have since disabled that menu item but the problem remains. 

I would very much like to stop Nautilus opening this extra window.

I've tried looking through gconf-editor but haven't seen anything that looks relevant. 

The extra window doesn't get opened when I run Nautilus from other places, but it always happens when Nautilus is opened from the Places Menu, regardless of whether I'm opening a drive or a bookmark. 


System is Karmic Koala running Gnome.

Thanks for any help.

---

### Post by andrewkirk on 2010-05-22
OK. I found a fix. I did the commands set out in the following link to re-set Gnome, and the problem disappeared.

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

