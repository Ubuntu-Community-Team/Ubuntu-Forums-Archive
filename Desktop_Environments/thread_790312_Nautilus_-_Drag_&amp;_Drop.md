---
title: "Nautilus - Drag &amp; Drop"
date: 2008-05-11
forum: Desktop Environments
---

### Post by Doomsword on 2008-05-11
Hi everyone. I've got a problem with Nautilus: if a open file-roller and drag&drop a file to a folder F-R doesn't unzip it. In the same way if I open folder "Background and emblems" and drag-drop a theme (or color) to a folder it won't change. The same problem was in ubuntu 7.10 (and maybe in 7.04).
I've done a full reinstall with my old home folder mounted on a separate partition. Please tell me if it's a ubuntu (BIG) problem or maybe there's something to reset in my home folder. Thank you in advance!!!

Fabio

---

### Post by Doomsword on 2008-05-11
Hi everyone! I created a new user and everything is fine. So I renamed my ~/.gconf folder in ~/--.gconf, log out and log in and resolved the problem. One thing I cannot get to work is creating new templates for nautilus context menu: I've got a ~/Templates folder but if I add files the menu always show me "No templates installed". There's maybe an old folder in my home directory that can conflict with my new 8.04 installation?
One strange thing is that clicking in nautilus "Go -->  Templates" always throw me in ~/ folder instead of ~/Templates. Anyone can help me? Thanks in advance!!

Fabio

---

### Post by Wolki on 2008-05-12
> **Doomsword said:**
> 
One strange thing is that clicking in nautilus "Go -->  Templates" always throw me in ~/ folder instead of ~/Templates. Anyone can help me? Thanks in advance!

Please post the contents of your ~/.config/user-dirs.dirs file.

---

### Post by dcontard on 2008-11-07
> **Wolki said:**
> Please post the contents of your ~/.config/user-dirs.dirs file.

Thanks for the tip Wolki! I had the same problem as Doomsword. After I changed the line ```
XDG_TEMPLATES_DIR="$HOME"
``` with ```
XDG_TEMPLATES_DIR="$HOME/Templates"
```, everything worked perfectly :D

---

