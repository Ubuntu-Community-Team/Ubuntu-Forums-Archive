---
title: "gnome-terminal --hide-menubar"
date: 2018-09-25
forum: Desktop Environments
---

### Post by Skaperen on 2018-09-25
my startup script sequence starts gnome-terminal on 2 of the 12 users i start up when i boot up my Ubuntu 16.04.5 LTS system where all users are still using Unity.

the user "admin" starts first and 7 terminals are started there, and later the user i do most things, like software development on, "pdh" (my initials) also gets 7 terminals.  on each, 3 workspaces get a terminal sized for almost the full display (profile name "termone", 166x46) and 2 workspaces each get 2 terminals situated side-by-side (profile name "termtwo", 82x46).

what has been happening is that on user "admin", these terminals start up with the terminal menubar displaying. but on user "pdh" it does not.

i was able to fix this by adding the command option [FONT=courier new]--hide-menubar[/FONT] as described in _[FONT=courier new]man gnome-terminal[/FONT]_.  i never use that menu bar.  it also cases those terminals to ha one fewer row (166x45 and 82x45).  the profile configuration has no means to choose the menubar.

my curiosity is: **what could cause the menubar to appear for "admin" and not for "pdh" without it being specified?**

---

