---
title: "Cairo-Dock issues"
date: 2009-02-17
forum: Desktop Environments
---

### Post by tmpname on 2009-02-17
I have just installed cairo-dock and anytime I try to launch it from run application all I get is a black box in my upper left hand screen for a few seconds then it disappears. 

When I run it from a terminal window I get these warnings.

Any help with this is greatly appreciated.

```

Xlib:  extension "RANDR" missing on display ":0.0".
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:1120)  
  Sorry but your X server does not support the extension.
 You can't have window thumbnails in the dock
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/elguapo/.config/cairo-dock/current_theme/background-cairo-dock.jpg': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/pico/.cairo-dock/current_theme/launchers/ooo-draw.png': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/elguapo/.config/cairo-dock/current_theme/background-cairo-dock.jpg': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/elguapo/.config/cairo-dock/current_theme/background-cairo-dock.jpg': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/elguapo/.config/cairo-dock/current_theme/background-cairo-dock.jpg': No such file or directory

```

---

