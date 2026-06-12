---
title: "Help, can't start gnome"
date: 2005-05-16
forum: Desktop Environments
---

### Post by iakie on 2005-05-16
I can't login into gnome anymore! this is how I got there:

I was trying to put a uniformed look & feel between gnome and kde app's, since I do use some KDE app's, and the default look with QT alone is absolutely aweful. 

At first I tried to use qt-config, however, the theme available looks so bad. So I decided to install Kcontrol. 

To have a uniformed look and feel, I also used gtk-qt theme engine. now nightmare begines. 

1) use Theme in gnome-panel, I made a custom theme, w/ GTK-QT as the engine. And now everything looks aweful (default QT theme).
2) use Kcontrol (under normal user, ie. not "sudo kcontrol"), I changed the default QT theme to plastik. Then, firefox and verious app's now have a KDE look. but, applets and gnome-panel crashes. after gnome-panel restarts, it still looks aweful, same goes w/ synaptic.
3) so w/ a tip from the forum, I copied .gtkrc and .gtk-qt-engine-rc to /root folder. now, I can't login to gnome anymore!!! fail-safe mode also doesn't work! Everytimes I try to login It's just a black screen and GDM gives a warning saying that I loged out within 10 seconds. In fact, I'm using my backup openbox session to write this.

Anyone has any idea what to do now?

---

### Post by compmodder26 on 2005-05-16
Not sure if this is the problem, but when this happens to me it is usually caused by the .ICEauthority file reverting it's permissions to root.  This file is located in your home directory.  Simply open a failsafe terminal and chown the file back to your ownership:

```
$ sudo chown <yourusername>:<yourusername> /home/<yourusername>/.ICEauthority
``` 

Obviously change <yourusername> to the username you are trying to log in as.

Hopefully this will do the trick.

---

