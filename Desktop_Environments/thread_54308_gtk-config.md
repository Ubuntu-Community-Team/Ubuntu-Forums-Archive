---
title: "gtk-config"
date: 2005-08-04
forum: Desktop Environments
---

### Post by [pl]ice on 2005-08-04
hi, i'm trying to compile kadu , polish chatting program, but to some reason this jumps out, that i don't have gtk-config; i'm not that sure what what is it for/where to get it.
any sugesstios?
thanks

---

### Post by d_weil_e on 2007-07-20
GTK stands for GIMP Toolkit.  It's used for developing X-Windows apps.  Ubuntu Feisty comes with libgtk2.0 which doesn't seem to contain the gtk-config program.  Install libgtk1.2-dev.  That contains gtk-config.

sudo apt-get install libgtk1.2-dev

That should fix ya up.

This was a really old post and happened to be the first link when I googled for the same problem.  Thought I'd post the solution in case someone else googles for the solution again.

---

### Post by Mazen on 2007-08-25
i've just had the same problem and used this fix, but now the installation is giving me 
> configure: error: OpenObex library version is too old.

any ideas?
thanks

---

