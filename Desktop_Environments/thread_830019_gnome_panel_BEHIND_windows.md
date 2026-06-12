---
title: "gnome panel BEHIND windows"
date: 2008-06-15
forum: Desktop Environments
---

### Post by billybag on 2008-06-15
For some odd reason my gnome panel likes to unhide BEHIND all my windows every so often and it is REALLY annoying. Any ideas?

---

### Post by pytheas22 on 2008-06-15
I'm not sure what could be causing it, but you might take a look at the /apps/panel settings in gconf-editor (press alt-f2 and type gconf-editor).

---

### Post by jerwilkins on 2010-03-09
I get the same issue. 
Only happens once in a blue moon, but when it does, I have to restart.
This is on fully up-to-date Karmic. Plumbing the gnome-config depths hasn't yielded a fix yet. Any notions, anyone?

---

### Post by pytheas22 on 2010-03-09
> I get the same issue.
Only happens once in a blue moon, but when it does, I have to restart.
This is on fully up-to-date Karmic. Plumbing the gnome-config depths hasn't yielded a fix yet. Any notions, anyone?

Still not sure what would cause that, but the next time it happens, try opening a terminal and typing "killall gnome-panel"  See if that solves the problem without forcing an entire reboot.

If you wanted, you could also launch gnome-panel from within a terminal (by typing "gnome-panel --replace" and see if any useful debugging output gets dumped to the terminal when you experience the behavior in question.

---

