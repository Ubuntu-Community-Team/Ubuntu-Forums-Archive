---
title: "Cannot change desktop from Home directory"
date: 2009-11-02
forum: Desktop Environments
---

### Post by bnebb on 2009-11-02
I installed Ubuntu 9.10 as a fresh install.  Installed kdebase-bin so I can run a few KDE apps I'm used to including Kate, Kontact, and Krusader (about all).  Everything else is stock Gnome.

Everything is OK until I activated the Nvidia proprietary drivers.  Then, my desktop changed to my Home directory.  Very cluttered with folders, etc.

I've tried using gconf-editor to set the nautilus preferences to show the Desktop folder instead of the home folder. I've tried editing the .config/user-dirs.dirs file.  It gets set back to a default on every reboot.  I've checked the XDG defaults file.  It shows the default Desktop to be the Desktop directory.  The Desktop directory gets deleted on every reboot so there is nothing to show.

Can't figure out what deleting the Desktop directory.  I've tried recreating it.  It recreates until the next boot.

Any suggestions?

Bnebb

---

