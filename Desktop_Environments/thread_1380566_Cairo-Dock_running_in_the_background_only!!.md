---
title: "Cairo-Dock running in the background only?!?!"
date: 2010-01-13
forum: Desktop Environments
---

### Post by PepeLapiu on 2010-01-13
Okay, this is a cross-post from the absolute beginner forums but I wasn't getting any answers there. 

I installed Cairo Dock a few weeks ago but un-installed it a few days later, still it appeared to be working fine back then.

Now I re-installed it just tonight via terminal.
But when I clicked on the icon, nothing happened, so I clicked again and nothing happened again. Then I started it from the terminal and here is the result:

```
pepelapiu@pepelapiu-laptop:~$ cairo-dock -o
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-switcher.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-Dbus.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
OpenGL version: 2.1 Mesa 7.6
OpenGL vendor: Tungsten Graphics, Inc
OpenGL renderer: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
WARNING: Application calling GLX 1.3 function "glXCreatePbuffer" when GLX 1.3 is not supported!  This is an application bug!
if your drivers are crappy, we'll know it immediately ...do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
 ok, they seem fine enough.
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/pepelapiu/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
(null) -> -1;-1
cairo_dock_refresh_launcher_gui ()

VERIFIER LE CHANGEMENT DE CONTAINER POUR TERMINAL
```

So I looked into the System Monitor to see which processes are running. Turns out I have two instances of Cairo-Dock running but I can't find any windows or dock to that effect. Cairo-Dock appears to be running in the background with no icons, windows, docks or applets of any kind to be seen, no visual indication at all that Cairo-Dock is running at all.

Where is my Cairo-Dock? How can I correct this problem?

Cheers,
PepeLapiu :)

---

### Post by matttbe on 2010-01-20
Hi,

I see that you use an old version of Cairo-Dock (one from Karmic repository but we can't update it, look at this bug : [#460001]("https://bugs.launchpad.net/ubuntu/+source/cairo-dock/+bug/460001")

Can you test the latest stable release from our [ppa]("https://launchpad.net/~cairo-dock-team/+archive/ppa")

If you still have this bug, can you test with this command : ```
cairo-dock -o -a
``` and test the latest RC release from this ["*weekly*" ppa]("https://launchpad.net/~cairo-dock-team/+archive/weekly") ?
For any other problem, can you go to [our forum]("http://cairo-dock.vef.fr/bg_forumlist.php")

Thanks ;)

---

