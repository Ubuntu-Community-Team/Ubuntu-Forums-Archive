---
title: "Compiz in Xubuntu 12.04"
date: 2012-06-06
forum: Desktop Environments
---

### Post by Denco1 on 2012-06-06
Hello all (again),
I think, that is not the first topic about this problem, but unfortunatelly I still have not found a solution.
I would like to use some effects from compiz, but the problem is, that effects do not work in xfwm4. When I change to compiz, they do work, but title bar of windows is gone.
Is there any working solution or should I wait for upgrade?
Thanks for your replies.

---

### Post by LewisTM on 2012-06-06
You have Compiz installed and know how to run it. That's good. All you need now is to install CompizConfig Settings Manager. Run it and enable the important plugins:
Composite
Move Windows
Resize Window
Window decorations

The rest is up to you.

Cheers!

---

### Post by LewisTM on 2012-06-07
Just thought of something.
If you are missing window borders, commonly called decorations, you might be missing the gtk-window-decorator.
This program is found in the compiz-gnome package
Then in the CompizConfig Settings Manager/Window Decoration, make sure the Window decorator command is
```
gtk-window-decorator --replace
```

---

### Post by Denco1 on 2012-06-07
Kind of working. Everytime I open a window, that is not full screen size, it appears at the very top of the screen, so I have to move it to see title bar (it is hidden behind my top panel).

---

### Post by LewisTM on 2012-06-07
Enable the Place Windows plugin and pick Smart Placement Mode.

---

### Post by Denco1 on 2012-06-07
Now woking nice. Thank you very much (sometimes when I maximize a window, it is not active but that is just little detail).

---

