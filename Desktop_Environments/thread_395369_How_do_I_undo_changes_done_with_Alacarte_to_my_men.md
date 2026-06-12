---
title: "How do I undo changes done with Alacarte to my menu layout?"
date: 2007-03-28
forum: Desktop Environments
---

### Post by sup on 2007-03-28
Hello, I have been using Alacarte heavily to customize my menus. However, I feel a little bit overwhelmed with my changes and I would like to change from scratch from the default layout. How do I do it?
I mean, from what I gathered by googling, manu layouts in GNOME are located in to places, one system wide, one user-wide, I guess that removing the user-wide directory with config settings would be enough, but I am not sure
1) where this directory is
2) if there is not something other that is important but unrelated to menu layout
3) if Alacarte is making changes only on this directory (if that directory even exists)

I tried to find some documentation about alacarte, but find almost none (a useless man page), sadly

---

### Post by sup on 2007-03-28
Hm, there is some info in GNOME 2.14 Desktop System Administration Guide
/ Customizing Menus
it says that user files are in ~/.config and ~/.local/share
But I am still not sure how alacarte treats these...

---

### Post by sup on 2007-05-06
so if one removes or moves ~/.config and ~/.local/share the original menus are restored

---

### Post by sup on 2007-05-06
and there is also a reverse button in alacarte now. I only hope it was not there before...

---

