---
title: "OSX Theme Removal"
date: 2009-04-11
forum: Desktop Environments
---

### Post by MarkM06 on 2009-04-11
Hey everyone,

Recently I followed this tutorial [http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11) to change the visual style of GNOME in Ubuntu 7.10. I'm happy with the theme itself, however, one of the other programs that came with it I don't like, it adds a File, Edit, View, Go, Bookmarks, and Help box to the top left of most windows, it's very annoying and ugly. Can someone help me figure out how to uninstall it?

Thanks a lot,
Mark

---

### Post by andrea000 on 2009-04-11
Just go to your and change your theme back to the ubuntu human
theme or one that you like.

---

### Post by balaknair on 2009-04-11
That would be the mac global menu. From what I could understand, it's a GTK hack plus a panel applet.

If you installed it following instructions here [http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868) the instructions to disable the GTK mod are given there as well
> Environment variable GTK_MENUBAR_NO_MAC let you set a list app executable names to disable mac menubar for, separated by space (default "gnome-panel acroread"). Set it to 1 to completely disable mac menubar.


To remove the applet from the panel> right click on the menu> select 'remove from panel'

Uninstalling- might be trickier, since I assume you used a .deb file and not Synaptic. If you know the package name, try 'sudo apt-get remove *package_name*' in a terminal. But be careful, and don't try it if you're not sure about the exact name. Uninstalling the wrong package can totally screw up your current install.

---

