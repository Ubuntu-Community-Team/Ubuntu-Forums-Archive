---
title: "Conky as right-hand side panel"
date: 2009-11-29
forum: Desktop Environments
---

### Post by Henry Flower on 2009-11-29
Is there any way to set conky as a panel on the right-hand side of the desktop, so that maximised windows don't cover it?   I've tried using 'own_window_type panel', but then maximised windows go below conky's bottom edge, not to the left of it.

---

### Post by Henry Flower on 2009-11-29
Bump for an answer to myself.  A horribly kludgy way to do it:

with conkyrc set to 

# own window options
own_window		yes
own_window_transparent	yes
own_window_type desktop
#own_window_hints undecorated,skip_taskbar

plus sidebar screenlet set to align right reserved and transparent, the screenlet sets to the right width aligns its right edge with the left edge of conky.   Maximised windows then extend to the right-hand edge of the screenlet, and the only evidence of the screenlet's existence is its left-hand edge.   Not ideal, but better than nothing.

---

### Post by Henry Flower on 2009-11-29
double post

---

