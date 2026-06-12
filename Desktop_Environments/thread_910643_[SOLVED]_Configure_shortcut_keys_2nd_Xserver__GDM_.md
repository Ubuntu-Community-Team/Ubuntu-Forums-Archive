---
title: "[SOLVED] Configure shortcut keys 2nd Xserver / GDM (Hardy 8.04)??"
date: 2008-09-04
forum: Desktop Environments
---

### Post by biriachan on 2008-09-04
Currently I play most of my video games on a 2nd Xserver session using WINE.  In the past I have reconfigured my gnome desktop shortcut to remove the ***keyboard combination <ALT> + (Right Mouse Click),*** and have remapped the shortcut to <Super> + <Shift> + (Right Mouse Click).

What should I do to change/disable this key combination on my 2nd Xserver Session?

I believe the keyboard shorts are mapped to Xserver and not GDM, because I only load the game Full screen using WINE, with no desktop or windows manager, but I could be wrong about that.

My 2nd Xserver must be pulling down the default shortcut configuration from somewhere, but I have no idea which files control this.

Anyone have any ideas of how to address this problem.


Edit ----

I found a fix for this on my own after reading the gconf-editor help file (what a shock!:)).

In order to set my new key-bindings as default for all users I ran 
```
gksu gconf-editor
```

File -> New Default Window

apps -> metacity:
mouse_button_modifier, Value set to <Super><Shift>.  Changed from original <ALT>

Now I no longer have the nasty problem up a pop up menu with playing Warcraft 3 and World of Warcraft on the 2nd X Server session!!

---

