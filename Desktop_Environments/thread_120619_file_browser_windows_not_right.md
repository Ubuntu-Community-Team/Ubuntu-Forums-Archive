---
title: "file browser windows not right"
date: 2006-01-23
forum: Desktop Environments
---

### Post by jtpratt on 2006-01-23
This seems like such a simple thing, and yet I cannot figure out how to make it right.  I've been using Breezy 5.10 for 3 months now, and when I first installed it the file browser windows had 2 features I liked:
- ever click to sub-folders opened in the same window (not new windows)
- the toolbar at the top, especially to go up or back one or more levels

Something I have done has made every click open yet another file browser window, and the toolbar is no longer there.  I have checked every single preference I can find with no luck.

Can you help me restore my file browser windows to their original default appearance and behaviours?

Thanks in advance if you can.

---

### Post by Wolki on 2006-01-23
Well, I personally don't know why someone would want that... but then I'm a big fan of spatial nautilus. 
Anyway, you probably need to open nautilus' preferences, click the "Behavior" tab, then check "always open as browser".

---

### Post by towsonu2003 on 2006-01-23
dont have my ubuntu install with me, but I remember a configuration editor under either one of these: 
Applications>System Tools
System>Administration>
System>Preferences
Once you open that configuration utility thingy, find nautilus in it and check out the options you have in there. sorry not so helpful...

---

### Post by Wolki on 2006-01-23
[QUOTE=towsonu2003]dont have my ubuntu install with me, but I remember a configuration editor under either one of these: 
Applications>System Tools
System>Administration>
System>Preferences
Once you open that configuration utility thingy, find nautilus in it and check out the options you have in there. sorry not so helpful...[/QUOTE]

Configuration Editor is under Applications>System Tools. and yes there are a lot of settings to fine tune the behavior of nautilus. Changing from Spatial to Browser and back, however, is possible completely from the GUI since Gnome 2.8, under Nautilus Preferences>Behavior.

If someone does want to use gconf_editor for it, though, the key is /apps/nautilus/preferences/always_use_browser

---

### Post by jtpratt on 2006-01-23
the always open in a browser window fixed it all.......thanks!

---

