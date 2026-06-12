---
title: "compiz on 13.04"
date: 2013-04-26
forum: Desktop Environments
---

### Post by vectorthorn on 2013-04-26
any one figure out how to get the desktop cube working for compiz on xubuntu 13.04?

compiz IS starting just fine, and i disabled desktop-wall and enabled desktop-cube and rotate-cube, but it's not working, and i was wondering if i am the only one with this issue.

fwiw, i UPGRADED from 12.10, instead of installing from scratch

oh, and, the most OBVIOUS problem: CCSM is NOT saving the changes i make - every time i open it again, the desktop-wall is checked and the desktop-cube and rotate-cube is unchecked again.

---

### Post by dentaku65 on 2013-04-26
Did you choose the flat-file configuration Backend under Preferences in CCSM?

---

### Post by vectorthorn on 2013-04-26
i switched the config from flat-file to gconfig, and now the settings stay the same, but the cube still does not work.

=== EDIT ===

got it! you have to switch it from flat-file (initial setting) to gconfig and back to flat-file again, then log out and it will work again when you log in.

---

