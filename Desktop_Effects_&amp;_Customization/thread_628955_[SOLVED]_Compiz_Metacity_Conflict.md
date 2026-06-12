---
title: "[SOLVED] Compiz/ Metacity Conflict"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by zoso375 on 2007-12-01
One of my favorite features of GG is the customization...Compiz is great, when it works.  The particular feature I'm having trouble with is the window transparency enabled by alt+mousewheel on each individual window.  When I enable this feature, it works, but I lose window borders, i.e. no minimize, maximize, or close option.  To get the windows back, I use "replace --metacity".  But, of course, as soon as I do that, I lose the window transparency ability again.  Any ideas on how to make this feature and metacity coexist?

---

### Post by zoso375 on 2007-12-01
I might have stumbled onto something, though I can't tell if it's directly related.  Compiz has Mesa installed (not nVidia).  Does anyone know if this is related?  If so, any tutorials out there on how to replace Mesa with nVidia?

---

### Post by reja on 2008-01-25
I have a similar problem. I have Compiz set up with various effects, but I have no windows titlebar (min, max, etc). When I run "metacity --replace", I get the title bar back, but I lose most of the Compiz functions, and terminal does an infinite loop of the following error:

"Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed"

AMD Athlon processor
NVIDIA Quadro NVS 280 SD
2.6.22-14-rt

thanks!

---

### Post by DaymItzJack on 2008-01-26
compiz --replace && metacity --replace

In Alt+F2

---

