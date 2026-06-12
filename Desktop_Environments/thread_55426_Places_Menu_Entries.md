---
title: "Places Menu Entries"
date: 2005-08-08
forum: Desktop Environments
---

### Post by acascianelli on 2005-08-08
I have a "Documents" entry in the Places menu, I do not want it there, how can I remove it.

Thanks.

---

### Post by Sam on 2005-08-08
If the folder ~/Documents exists, it'll appear in the places menu. You have to rename it to something else.

Maybe there is a differtent way to get rid of it.

---

### Post by acascianelli on 2005-08-08
[QUOTE=Sam]If the folder ~/Documents exists, it'll appear in the places menu. You have to rename it to something else.

Maybe there is a differtent way to get rid of it.[/QUOTE]

Ok, heres what I did.  When I first installed Ubuntu, I created a folder called "My Documents".  Today I renamed it to "Documents", that why It must have appeared, but now when I change it back to something else, the entry still remains.

---

### Post by acascianelli on 2005-08-09
[QUOTE=acascianelli]Ok, heres what I did.  When I first installed Ubuntu, I created a folder called "My Documents".  Today I renamed it to "Documents", that why It must have appeared, but now when I change it back to something else, the entry still remains.[/QUOTE]
 Nevermind, I tried renaming and rebooting again and its gone now.  Thanks.

---

### Post by charlieg on 2005-08-09
You probably only needed to restart gnome-panel (just a 'killall gnome-panel' in a terminal) but I guess it's a moot point now.

---

### Post by juancnuno on 2005-10-27
Is there a way to remove the entry without having to rename the Documents folder?  I think whatever causes that entry also makes the file chooser always open in Documents.  I'd much much rather keep my folder name, remove the Places item right above Computer, and have the file chooser open in home, not Documents.

---

### Post by Alexander Kirillov on 2005-10-27
[QUOTE=juancnuno]Is there a way to remove the entry without having to rename the Documents folder?  I think whatever causes that entry also makes the file chooser always open in Documents.  I'd much much rather keep my folder name, remove the Places item right above Computer, and have the file chooser open in home, not Documents.[/QUOTE]
I do not think it is currently possible. Maybe we should file a bug in GNOME database (against component gnome-panel).

---

### Post by juancnuno on 2005-10-27
I was under the impression that that Documents behavior was an Ubuntu patch of Nautilus or whatever, and not the default GNOME behavior.  Maybe we can download unpatched versions?  Or file a bug in the Ubuntu database instead?

---

### Post by Alexander Kirillov on 2005-10-27
[QUOTE=juancnuno]I was under the impression that that Documents behavior was an Ubuntu patch of Nautilus or whatever, and not the default GNOME behavior.  Maybe we can download unpatched versions?  Or file a bug in the Ubuntu database instead?[/QUOTE]
Honestly, I do not know. 
We may add our comments to [GNOME bug 310050](http://bugzilla.gnome.org/show_bug.cgi?id=310050)

---

