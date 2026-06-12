---
title: "Disabling maximize-when-dragged-to-edge behavior?"
date: 2011-06-08
forum: Desktop Environments
---

### Post by dankegel on 2011-06-08
I use a laptop and several windows.  I often move the windows
around on the screen so I can see them all.  Unfortunately,
this often causes the windows to maximize when I didn't want 
them to.

I think in Unity the way to turn this off is
  1. install ccsm
  2. search for snap in ccsm
  3. disable it

but since I am using the 2d fallback instead of Unity,
that doesn't work.  How does one turn this feature off in the
2d window manager?

---

### Post by Copper Bezel on 2011-06-09
It doesn't work by default in the 2D window manager (Metacity.) Are you sure you aren't running Compiz? Using the Classic desktop doesn't actually mean you're not using Compiz; even "Classic - No Effects" can be reconfigured to run Compiz, and you could have done that by accident.

The window snapping is called the Grid plugin, and it is indeed a feature of Compiz. Disable it in CCSM, and it shouldn't happen again. There's no equivalent feature under Metacity.

---

### Post by philinux on 2011-06-10
> **Copper Bezel said:**
> It doesn't work by default in the 2D window manager (Metacity.) Are you sure you aren't running Compiz? Using the Classic desktop doesn't actually mean you're not using Compiz; even "Classic - No Effects" can be reconfigured to run Compiz, and you could have done that by accident.

The window snapping is called the Grid plugin, and it is indeed a feature of Compiz. Disable it in CCSM, and it shouldn't happen again. There's no equivalent feature under Metacity.

Thank you for that. The grid plugin under Window Management was causing this. Moving anything to the top of the screen was resizing the app.

PITA on my laptop mainly that was. :p

---

