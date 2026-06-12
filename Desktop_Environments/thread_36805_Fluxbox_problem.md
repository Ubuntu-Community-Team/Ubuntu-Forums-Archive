---
title: "Fluxbox problem"
date: 2005-05-24
forum: Desktop Environments
---

### Post by SparkyDawg on 2005-05-24
Today I've decided to give Fluxbox a try, and ran into a problem very early on.

I installed it from Synaptic, than ran it from GDM, works fine. Except I have to add all the apps to the menu by running fluxmenu. When I try to run fluxmenu in xterm, I get a "Can't open /fluxbox/fluxbox-menu : No such file or directory Please, change the menu location with fluxconf to a writable one. (E.g ~/.fluxbox/fluxbox-menu) 

I tried what xterm said, but no cigar.

Any help?

---

### Post by s7eam on 2005-05-24
[QUOTE=SparkyDawg]Today I've decided to give Fluxbox a try, and ran into a problem very early on.

I installed it from Synaptic, than ran it from GDM, works fine. Except I have to add all the apps to the menu by running fluxmenu. When I try to run fluxmenu in xterm, I get a "Can't open /fluxbox/fluxbox-menu : No such file or directory Please, change the menu location with fluxconf to a writable one. (E.g ~/.fluxbox/fluxbox-menu) 

I tried what xterm said, but no cigar.

Any help?[/QUOTE]

Make ~/.fluxbox/fluxbox-menu file and rerun fluxmenu.

---

### Post by SparkyDawg on 2005-05-24
Didn't work, sadly.

---

### Post by Juippisi on 2005-05-24
Edit ~/.fluxbox/init file, so there is a line "session.menuFile:       /home/name/.fluxbox/fluxbox-menu"

I hope that works. Oh, and make sure that you have rights to that ~/.fluxbox/fluxbox-menu file.

---

