---
title: "Running AWN"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by Cubedude04 on 2007-07-30
Hey i seemed to have installed AWN 

I followed this guide
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
And did the SVN method. I followed all the steps but i can't work out how to actually run the AWN program.

Under system there is AVANT preferences and AFFINITY Preferences but they do not do anything when i click on then. I.e nothing pops up

How do i actually run AWN then

Thanks in advance :)

---

### Post by walkerk on 2007-07-30
in a terminal window type:
```
avant-window-navigator
```

if you want to load it at boot up then add it to your System > Preferences > Sessions:
```
Name: AWN
Command: avant-window-navigator
```

also you should see it under Applications > Accessories > Avant Window Navigator

---

### Post by Cubedude04 on 2007-07-30
That worked great thanks =D

And incase you saw it before i edited. i fixed the second problem =D

---

### Post by mysticmatrix on 2007-07-30
On terminal type
```
gconf-editor
```
This should open Gnome Configuration Editor.

---

