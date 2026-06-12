---
title: "Cairo Dock Errors"
date: 2009-02-06
forum: General Help
---

### Post by mpl34 on 2009-02-06
Hey i would appreciate knowing if the following is a major issue or not? Also i noticed a few gnome apps that are very useful and was wondering if there were updates/plugins similar for a KDE environment.

Heres the errors that are concerning, the dock still seems to run tho.
```
michael@michael-laptop:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)      
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-gnome-integration-old.so' : (libgnomeui-2.so.0: cannot open shared object file: No such file or directory)    
libbonoboui-2.so.0: cannot open shared object file: No such file or directory   
libbonoboui-2.so.0: cannot open shared object file: No such file or directory   
cairo_dock_get_desklet_decoration (personnal)                                   
cairo_dock_create_surface_from_image: assertion `rsvg_handle != NULL' failed    
warning :  (cairo-dock-load.c:cairo_dock_load_task_indicator:787)               
  couldn't load image '/home/pico/.cairo-dock/Indicateur cairo dock/1208712452.svg' for indicators                                                              
nouvelle icone d'appli (31457352)                                               
nouvelle icone d'appli (31457313)                                               
nouvelle icone d'appli (39845932)                                               
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)                                                                        
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.                                     
 insertion de KTorrent apres Maintenance -> iSeparatorType : 1
nouvelle icone d'appli (56623105)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)
  This pixmap is undefined. It can happen for exemple for a window that is in aminimized state when the dock is launching.
nouvelle icone d'appli (44040194)
iRotation:0°
decorations : default
 insertion de Meteo apres michael : bash -> iSeparatorType : 3
iRotation:0°
decorations : default
iRotation:0°
decorations : default
iRotation:0°
decorations : default
iRotation:0°
decorations : default
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)
  Failed to open file '/home/michael/.cairo-dock/current_theme/launchers/dustbin-empty.png': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)
  Failed to open file '/home/michael/.cairo-dock/current_theme/launchers/dustbin-full.png': No such file or directory
warning :  (applet-init.c:_load_theme:72)
  Attention : couldn't find images, this theme is not valid
warning :  (cairo-dock-modules.c:cairo_dock_activate_modules_from_list:291)
  No such module (gnome integration)
  MaJ des decorations du fond -> 1000.00x38.00
add personnal
add default
add personnal
weather : applet : a053ed0, icon : a040b00, subdock <- a351cf8

```

---

### Post by mpl34 on 2009-02-06
The following error keeps re-appearing in the terminal when cairo-dock is running. Also although it is running there is no sign of it running on my desktop.

```
This pixmap is undefined. It can happen for exemple for a window that is in aminimized state when the dock is launching.
cairo_dock_window_is_fullscreen_or_hidden_or_maximized ()
changement d'etat de 39845932 => {0 ; 0 ; 0 ; 0}
new backing pixmap (bis) : 79691796
cairo_dock_window_is_fullscreen_or_hidden_or_maximized ()
changement d'etat de 39845932 => {0 ; 1 ; 0 ; 0}
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)
  This pixmap is undefined. It can happen for exemple for a window that is in aminimized state when the dock is launching.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:125)
  This pixmap is undefined. It can happen for exemple for a window that is in aminimized state when the dock is launching.
```

---

### Post by mpl34 on 2009-02-07
Still having this problem however i have been able to get it running with crashing every 2nd min. One problem is that is just doesn't seem to perform nicely, i have ran dock in vista before and they have ran alot smoother than what i am finding with this cairo dock. 

I would also like to know if there are specific files or plugins that are specifically designed for a gnome environment that should be removed for a KDE environment that would improve its performance.

---

