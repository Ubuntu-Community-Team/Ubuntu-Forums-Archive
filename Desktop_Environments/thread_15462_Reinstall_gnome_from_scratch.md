---
title: "Reinstall gnome from scratch?"
date: 2005-02-14
forum: Desktop Environments
---

### Post by nesr on 2005-02-14
Hi all,

I was really happy with ubuntu untill i tried xfce4, and it  up my system pretty good. xfce runs great but i gnome is all in the ditch now. My menus is completely messed up and nautilus comes with a bunch of errors if i try to start up gnome..

So simply as the title spells out; How can i completely purge all config-files from gnome and install it from scratch? (from the installation CD will also be fine)..

Any help will be appreciated.

This really sucks! :/

---

### Post by scoon on 2005-02-14
Hey there, 

All you need to do is remove these directories in your $HOME directory:

.gconf, .gconfd, .gnome, .gnome2, .gnome_private, .gnome2_private, .metacity, .nautilus

scoon

---

