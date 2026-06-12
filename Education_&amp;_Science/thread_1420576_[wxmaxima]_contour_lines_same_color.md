---
title: "[wxmaxima] contour lines same color"
date: 2010-03-03
forum: Education &amp; Science
---

### Post by marbertone on 2010-03-03
Hi everybody!
By doing that (loading 'draw' first) contour lines are all green!!!
How could I fix that?

Thanx!
Mario Alberto

```

draw3d(terminal = wxt,
             file_name="/home/bertone/Scrivania/plot3",
             nticks = 120,
             enhanced3d = true,
             contour = base,
             user_preamble="set key off",
             contour_levels = [0,0.01,0.05],
implicit(y = g(f,x),
 x, 0.01,0.35, y, 0.01,1,f,0.01,0.04),
            
            )$

```

---

### Post by marbertone on 2010-05-25
Seems like it's not fixable in implicit_plot. I shall try on the new version, anyway... I mark it as solved!
M.A.

---

