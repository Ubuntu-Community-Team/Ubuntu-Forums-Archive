---
title: "Super Tux Kart launcher"
date: 2009-09-19
forum: Gaming &amp; Leisure
---

### Post by LinuxFox on 2009-09-19
I can't seem to get this working, whenever I make a launcher for Super Tux Kart under Applications > Games menu, it never works.  What do I need to do to get it working, I want it on my list of games please.

If it helps, I'm using the static binary version 0.6.2.  I know how to make launchers in the menu, but this one game is refusing to work as a menu.

---

### Post by Perfect Storm on 2009-09-20
You properly need to script it to the directory;

 sh -c "cd <distination> && ./<static binary>"


also make sure that static binary is set to executable

chmod +x <static binary>

---

### Post by LinuxFox on 2009-09-20
> **Artificial Intelligence said:**
> You properly need to script it to the directory;

 sh -c "cd <distination> && ./<static binary>"


also make sure that static binary is set to executable

chm +x <static binary>I did this and now the launcher is working like it should.  Both Games menu and the desktop.  Thanks a lot. 8)

---

