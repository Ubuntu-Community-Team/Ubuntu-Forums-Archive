---
title: "Widget padding messed up. Need urgent help!"
date: 2009-08-14
forum: Desktop Environments
---

### Post by Fzang on 2009-08-14
I was playing around with gnome color chooser to see what all the functions did. I stumbled upon widget padding which changes the size of buttons and menus. I didn't know what it did and I wanted to see an effect, so I set the y-padding to 10 and pressed apply.

...Now all buttons and menus have gained an extra 10 pixels which makes everything very big. I can't reset it because my screen is only 1280x800 and gnome color chooser window is bigger than that and CAN'T be resized! I've tried looking in the gnome color chooser gtkrc file but I can't find anywhere that says y padding = 10!

What do I do? Everything is so big and unusable!

---

### Post by galileolajara on 2009-08-14
This may help [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by SoftwareExplorer on 2009-08-14
Have you tried holding down ALT and dragging the window with the left mouse button so you can see and change the part of the window you need to?

---

### Post by JackTheDipper on 2009-08-15
Alternativeley just delete ~/.gtkrc-2.0-gnome-color-chooser and restart your applications or desktop.

(btw. it's called xthickness and ythickness in gtkrc language)

---

### Post by Fzang on 2009-08-15
Finally found that y thickness and changed it. Phew.

---

