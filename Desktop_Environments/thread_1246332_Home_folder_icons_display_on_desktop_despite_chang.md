---
title: "Home folder icons display on desktop despite changing gconf-editor"
date: 2009-08-21
forum: Desktop Environments
---

### Post by plr4ever on 2009-08-21
Hey all

I recently install Crunchbang linux 9.04 on my laptop, but soon got tired of the minimalism of openbox. I installed ubuntu-desktop, and i now have gnome working fine, except for one glaring problem:
the contents of my home folder are constantly displayed on my Desktop.

I've tried going into gconf-editor and ticking/unticking the box that should normally control this, logging out after each time, to no avail. 

I have also tried using ubuntu tweak to do the same thing, but it also failed to change anything.

Is there a config file somewhere that changes which directory nautilus displays on the desktop? Or some other work around?

Thanks!

Zach

---

### Post by aum11 on 2009-08-23
The following worked for me:

Edit ~/.config/user-dirs.dirs and set "XDG_DESKTOP_DIR" to "$HOME/Desktop".

---

### Post by plr4ever on 2009-08-27
Thank you SO much, I have been banging my head against the wall for ages now trying to fix that.

---

