---
title: "struggling with compiz 'fixed window placement'"
date: 2010-06-10
forum: Desktop Environments
---

### Post by olivine on 2010-06-10
I'm trying to start a transparent gnome-terminal in a specific viewport/workspace. I have 4 horizontal viewports and a gnome-terminal profile called transterm. In compiz 'Place windows', I set:
Window with fixed position  -> title=transterm, X pos = 30, Y pos = 30
Window with fixed viewport -> title=transterm, X viewport position = 4, Y viewport position=1.

when I type:
gnome-terminal --window-with-profile=transterm --title=transterm
in the CLI, it either doesn't start any terminal at all (if I'm not in the 4th viewport), or it starts it in all 4 viewports (if I'm in the 4th one). 

I've tried changing various settings to no effect. Any suggestions?

---

### Post by olivine on 2010-06-11
bump

---

### Post by olivine on 2010-06-13
I had the window listed in "sticky" in "window rules", which caused it to show up on every viewport. duh. ok now.

---

