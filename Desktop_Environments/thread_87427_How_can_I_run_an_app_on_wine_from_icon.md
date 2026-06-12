---
title: "How can I run an app on wine from icon?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Terrycymru on 2005-11-08
I've set up a "must have"  windows app to run on wine. It runs successfully from terminal but typing in the long path is a pain. Is there some way to run it from an icon? I haven't got into scripts yet but is this the way to do it?

---

### Post by Pablo_Escobar on 2005-11-08
It's easy.
There are 2 ways of doing this.
1. In nautilus right click on it, and in the fourth tab (as I recall) there should be "open with" or "preferred application".
If there is a Wine in the drop-down icon menu select it, or if not select other and type in "wine"
2. Easier way -> Create a new launcher -> Type in a new name -> and in the command part type in "wine /path/where/you/have/your/exe/file"

---

### Post by manicka on 2005-11-08
or you could make an icon in the gnome menus with smeg(Applications-->System Tools--.>Applications menu editor). As an example I use this command to start DVDShrink

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

---

