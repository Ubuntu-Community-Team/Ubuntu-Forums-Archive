---
title: "New theme crashing gnome desktop"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by flange_monkey on 2007-04-06
evening all

I applied a new theme to gnome which has caused multiple crashes, from a login, while the desktop is building.

I fixed this before by deleting a hidden directory, effectively setting gnome back to its default theme but I can't remember which directory it is.

Could someone please let me know coz it's beginning to get to me.

Cheers

Alan

---

### Post by yabbadabbadont on 2007-04-06
You probably need to remove the .themes directory in your home directory.  Note: the directory name starts with a period.

---

### Post by flange_monkey on 2007-04-06
Nope, I tried that one before and it didn't work. Also tried .gnome and .gnome2 without success.

Is there another way of changing a theme  as the theme manager crashes as well?

---

### Post by yabbadabbadont on 2007-04-06
Well, if you knew which registry keys to change, you could use gconftool from the command line.  I don't have gnome installed or I would find them for you.  Hopefully someone else reading this will do so.

---

### Post by mcduck on 2007-04-07
> **yabbadabbadont said:**
> Well, if you knew which registry keys to change, you could use gconftool from the command line.  I don't have gnome installed or I would find them for you.  Hopefully someone else reading this will do so.The right key is /desktop/gnome/interface/gtk_theme, just set it to name of theme you want to use (just the name, no path).

---

### Post by flange_monkey on 2007-04-08
Thanks all, that fixed it.

Alan

---

