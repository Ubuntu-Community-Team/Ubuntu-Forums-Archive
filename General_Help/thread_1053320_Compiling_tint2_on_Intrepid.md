---
title: "Compiling tint2 on Intrepid"
date: 2009-01-28
forum: General Help
---

### Post by dbbolton on 2009-01-28
I'm trying to compile version 0.6.0 of tint2 on intrepid. I'm pretty sure I have installed all the dependencies (including the dev packages). When I run make, i get this:

```

cc  -Wall -g `pkg-config --cflags --libs cairo pangocairo x11 xinerama imlib2 glib-2.0` -o tint tint.c server.c window.c task.c launcher.c visual.c config.c
server.c:31:35: error: X11/extensions/Xrandr.h: No such file or directory
make: *** [tint] Error 1

```

Does anyone know how to handle this?

---

### Post by dbbolton on 2009-01-28
> **dbbolton said:**
> I'm trying to compile version 0.6.0 of tint2 on intrepid. I'm pretty sure I have installed all the dependencies (including the dev packages). When I run make, i get this:

```

cc  -Wall -g `pkg-config --cflags --libs cairo pangocairo x11 xinerama imlib2 glib-2.0` -o tint tint.c server.c window.c task.c launcher.c visual.c config.c
server.c:31:35: error: X11/extensions/Xrandr.h: No such file or directory
make: *** [tint] Error 1

```

Does anyone know how to handle this?
It turns out I was missing one package:

```

 libxrandr-dev
[COLOR=#888888] 
```[/COLOR]

---

