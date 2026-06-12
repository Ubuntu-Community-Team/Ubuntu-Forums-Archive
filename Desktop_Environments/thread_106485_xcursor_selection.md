---
title: "xcursor selection"
date: 2005-12-20
forum: Desktop Environments
---

### Post by emerick7 on 2005-12-20
I'm trying to set up a new cursor theme for my comp, but haven't found the way to do so.  I followed a guide I found in the forums but that doesn't seem to work.  I downloaded the tar file for [crystal xcursors]("http://gnome-look.org/content/show.php?content=6240") and then went into cursor selection.  After clicking install theme, it goes through the archive manager extraction.  Back in the xcursor selection though, nothing new pops up.  Any ideas on how to fix this?

---

### Post by codejunkie on 2005-12-20
[QUOTE=emerick7]I'm trying to set up a new cursor theme for my comp, but haven't found the way to do so.  I followed a guide I found in the forums but that doesn't seem to work.  I downloaded the tar file for [crystal xcursors]("http://gnome-look.org/content/show.php?content=6240") and then went into cursor selection.  After clicking install theme, it goes through the archive manager extraction.  Back in the xcursor selection though, nothing new pops up.  Any ideas on how to fix this?[/QUOTE]
install gcursor with ```
sudo apt-get install gcursor
``` then you can change them by going to /System/Preferences/Cursor selection.

---

### Post by emerick7 on 2005-12-20
That's what I've been in.  I go into Cursor Selection, and then click "install theme."  I find the tar and that gets extracted.  When I go back into the Cursor Selection screen, nothing new appears.

---

### Post by codejunkie on 2005-12-20
[QUOTE=emerick7]That's what I've been in.  I go into Cursor Selection, and then click "install theme."  I find the tar and that gets extracted.  When I go back into the Cursor Selection screen, nothing new appears.[/QUOTE]
with normal cursor themes you just install with gcursor. with that theme that your trying to install you have compile them first open a terminal cd to that directory 
and run these commands in order 
```
make
```
```
sudo make install
```
then go to gcursor and they should be listed there.

---

### Post by emerick7 on 2005-12-20
got that to work (first time I've compiled something)... thanks!

---

