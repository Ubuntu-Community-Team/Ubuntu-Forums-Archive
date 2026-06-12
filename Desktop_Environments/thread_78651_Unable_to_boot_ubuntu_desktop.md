---
title: "Unable to boot ubuntu desktop"
date: 2005-10-18
forum: Desktop Environments
---

### Post by jdway on 2005-10-18
I recently added a few codecs and media players to my computer and now when I restart my computer it brings me to the terminal screen. It asks for my name and password but after I enter them it takes me to the terminal prompt and not my desktop. What command do I need to enter and how can I fix this in order to     have the desktop boot up instead of the command prompt.

---

### Post by ecobuntu on 2005-10-18
sudo startx

will invoke X to start.  So you can load into Gnome or KDE

but you might have some how screwed up something in xorg.conf.  
Do this first to make sure everything is fine in xorg

sudo dpkg-reconfigure xserver-xorg

Good Luck!

---

