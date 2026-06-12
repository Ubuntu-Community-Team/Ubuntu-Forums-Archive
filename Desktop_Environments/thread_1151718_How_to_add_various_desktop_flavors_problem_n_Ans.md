---
title: "How to add various desktop flavors problem? n Ans"
date: 2009-05-07
forum: Desktop Environments
---

### Post by joewski on 2009-05-07
I have been working on a desktop display system by creating a number of users each with there own desktop. Looking something like this.

Username     Desktop
desktop1     Gnome mixed up
desktop2     Gnome with Awn manager
desktop3     Gnome standard
desktop4     KDE4
desktop5     XFCE
desktop6     edubuntu
desktop7     ubuntustudio
etc

To make this work I would use the command
..
$ sudo apt-get install edubuntu-desktop
$ sudo apt-get install ubuntusudio-desktop
etc
Between each desktop install I would create a new user calling them desktopn. 

Anyway I've managed to go a long way with this but now I came across an effect which killed desktop1. 
To try and repair the desktop I used the following command from terminal

$ rm -rf .gconf .gconfd .metacity

Anyway this did the trick and reset the desktop unfortunately to the ubuntustudio desktop.

What I would like to do is somehow reset the default desktop back to the Gnome desktop without killing all the other desktops. It would also be handy to know how to change the default desktop to any distro flavour so that when new desktops are created they can be created from that base. In essence what I want to do is create a new user with a desktop based on the basic Gnome desktop (or any other desktop).

I plan to reset desktop1 by using command

$ rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Does anybody know how to change or switch the default desktop theme for a new user?

---

