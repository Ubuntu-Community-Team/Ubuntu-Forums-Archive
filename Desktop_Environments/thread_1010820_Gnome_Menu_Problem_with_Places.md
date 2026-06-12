---
title: "Gnome Menu Problem with Places"
date: 2008-12-14
forum: Desktop Environments
---

### Post by sombertattoo on 2008-12-14
So I feel like a newb...

So I was clearing out some entries in gnome-menu using Alacarte, deleting the old ones and it appears I've removed the nautilus entry (I think it was called "Open File") which now prevents me from using "Places" in the menu. If I click on say the home folder under "Places", I get Phatch popping up (my batch image editor) instead of Nautilus.

I can happily open Nautilus from terminal though.

If someone could post the settings for the "Open File" entry (or whatever it's called) so I can rebuild it, that would be greatly appreciated!! I think the critical entry I deleted was under Applications -> Other but I maybe wrong.

I've tried default menu entries by deleting the ~/.config/menus folder and either starting from defaults or replacing with a backed up version. No joy.

Btw, Intrepid, 64bit..though I doubt it would make a significant difference.

---

### Post by sombertattoo on 2008-12-14
Solved..I guess I hit the correct google search phrase.

[http://ubuntuforums.org/showthread.php?t=822007]("http://ubuntuforums.org/showthread.php?t=822007") Post #3. 

Simply delete the files in ~/.local/share/applications/ . When you edit a menu and delete entries, the entries are copied to ~/.local/share/applications for safe keeping. So, to recover lost entries, just delete whatever you need and the changes are immediate.

Thanks

MODS: please mark thread as solved

---

