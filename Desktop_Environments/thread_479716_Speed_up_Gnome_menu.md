---
title: "Speed up Gnome menu"
date: 2007-06-20
forum: Desktop Environments
---

### Post by decatett on 2007-06-20
"

The VnTutor weblog explains how to speed up your Gnome menus by removing the default delay. Open your text editor of choice and copy and paste in the following text:

    gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0 

Save the file into your home directory with the name .gtkrc-2.0 (don't forget the period before the filename), and restart your session (CTRL+ALT+BACKSPACE). You'll notice a nice speed boost when browsing within a category in your menu.  

"


[http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php](http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php)

---

### Post by Richard Kut on 2007-07-01
I believe that the proper command is

> echo "gtk-menu-popup-delay = 0" > ~/.gtkrc-2.0

---

