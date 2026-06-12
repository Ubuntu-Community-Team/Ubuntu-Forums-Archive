---
title: "Cairo-Dock2 : first release candidate !"
date: 2009-04-15
forum: Desktop Environments
---

### Post by fabounet on 2009-04-15
as usual, available on Berlios until the final release, which will then be available on the repository.
[http://developer.berlios.de/project/showfiles.php?group_id=8724]("http://developer.berlios.de/project/showfiles.php?group_id=8724")
this time 64bits packages are available ;-)

---

### Post by Scubdup on 2009-04-15
Ooo. Thanks for that. I've been wondering when this would be released. Been able to give it a whirl?

I find v1 overall excellent, but with a couple of clunky issues.

---

### Post by Mark76 on 2009-04-15
Can anyone explain this?

> cairo-dock
warning :  (cairo-dock-draw-opengl.c:cairo_dock_get_opengl_config:1654)  
  couldn't find an appropriate visual ourself, trying something else, this may not work with some drivers ...
gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
OpenGL version: 2.1 Mesa 7.4
OpenGL vendor: Mesa Project
OpenGL renderer: Software Rasterizer
redessin force ...
done.
 marges min: 5 | 5
 marges max: 0 | 0
redessin force ...
-> 10x8
warning :  (cairo-dock.c:_cairo_dock_intercept_signal:195)  
  Attention : Cairo-Dock has crashed (sig 11).
It will be restarted now.
Feel free to report this bug on cairo-dock.org to help improving the dock !
warning :  (cairo-dock-draw-opengl.c:cairo_dock_get_opengl_config:1654)  
  couldn't find an appropriate visual ourself, trying something else, this may not work with some drivers ...
debut de boucle bloquante ...


---

### Post by fabounet on 2009-04-15
please start the dock from the menu.
there should be 2 entries in System, choose the one without opengl in your case.

Also, don't forget to check in the help.

---

