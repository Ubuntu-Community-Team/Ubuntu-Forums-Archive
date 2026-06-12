---
title: "File (Nemo) Manager Window Stacking"
date: 2014-05-19
forum: Desktop Environments
---

### Post by makitso on 2014-05-19
Ubuntu Gnome 14.01, have Nemo installed (webupd8team ppa) and it controls desktop.  I have noticed that sometimes when I open Nemo, it opens behind the current window that is open.  This same thing does not appear to happen with Nautilus.  Looked through the options with dconf editor but nothing jumps out at me.  

Suggestions?

---

### Post by makitso on 2014-05-25
OK figured out what the problem is.  It has nothing to do with Nemo.  I was using Docky and it turns out that if launch a terminal app from the dock and then open Nemo or Nautilus from the dock, both windows open behind the terminal window.  I tried Plank and it has the same behavior.  I tried Cairo dock and it worked correctly.

---

