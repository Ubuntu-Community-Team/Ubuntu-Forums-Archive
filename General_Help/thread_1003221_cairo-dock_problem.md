---
title: "cairo-dock problem"
date: 2008-12-05
forum: General Help
---

### Post by dondad on 2008-12-05
I was running cairo in 8.04 and it worked fine. I tried it in 8.10 with no luck, but that was an early version, so I just used AWN. I prefer cairo, so tried it again. It installs, but when i try to run it I get:

```

warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/usr/share/app-install/icons/gnome-terminal.png': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/usr/share/app-install/icons/mobile_player.png': No such file or directory
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:123)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/usr/share/cairo-dock/themes/_MacOSX_/_x_.bg.png.png': No such file or directory


```

Any idea what is wrong?

---

