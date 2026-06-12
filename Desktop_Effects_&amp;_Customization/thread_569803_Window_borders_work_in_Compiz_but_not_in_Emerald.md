---
title: "Window borders work in Compiz but not in Emerald"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by dreamsR4living on 2007-10-07
Before my GTK window borders didn't work with Compiz. I fixed this with the following command; sudo nvidia-xconfig --add-argb-glx-visuals.

When I replace the GTK window manager with Emerald, my window borders disapear again. In Emerald only the corners of the window borders are working.

Is there anyone who knows how to fix this?

---

### Post by Sturmeh on 2007-10-08
Make sure "window decorations" are enabled in compiz manager.
Then "metacity --replace" and "emerald --replace" then "compiz --replace"...

Compiz uses emerald as a window decorator by default if it finds it.
Usually the problem is the other way around, using emerald to fix it.

---

### Post by DJ_Peng on 2007-10-08
> **Sturmeh said:**
> Make sure "window decorations" are enabled in compiz manager.
Then "metacity --replace" and "emerald --replace" then "compiz --replace"...

I managed to get Compiz working in Gutsy with the window borders by running this. Is there some way I can force this in Compiz Manager to get theis behavior by default? It's pretty annoying enabling the effects in either the Fusion Icon or in Appearances > Visual Effects and losing my borders.

Also, any new windows created after running the above sequence don't have the window borders.

---

