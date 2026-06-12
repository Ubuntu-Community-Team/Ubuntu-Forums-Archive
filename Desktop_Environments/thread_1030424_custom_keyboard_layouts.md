---
title: "custom keyboard layouts"
date: 2009-01-04
forum: Desktop Environments
---

### Post by argo82 on 2009-01-04
Hi!
I have a German keyboard but unfortunately a few characters I need regularly are missing. Therefore I'd like to modify the layout slightly, replacing unused symbols with the ones I need.
I tried to follow the tutorial here [http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html) but I can't find the configuration files needed. I guess it's obsolete or ubuntu has a different directory structure.

I looked here in the forum and figured out there is some software to download that one can use to generate new layouts, but I'd prefer just changing a configuration file because I really only need to make minor adjustments.
Is there a simple way to do this?
Thanks in advance!
argo82

---

### Post by argo82 on 2009-01-04
Alright, problem was that /etc/X11/xkb/base.xml seems to be completely ignored by gnome now.
I edited /usr/share/X11/xkb/rules/evdev.xml and it worked :-) 
Before I needed to add the layout details to /usr/share/X11/xkb/symbols/de

---

