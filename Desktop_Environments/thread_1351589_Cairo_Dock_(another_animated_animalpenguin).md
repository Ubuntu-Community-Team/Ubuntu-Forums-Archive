---
title: "Cairo Dock (another animated animal/penguin)"
date: 2009-12-10
forum: Desktop Environments
---

### Post by ChappyHappy on 2009-12-10
Hi, where can I get a plug-in for another animal similar to the penguin?

There's a fish looking one at <http://www.cairo-dock.org/ww_page.php?p=Our%20Themes%20%28an%20overview%29>. The theme is called "Brit".

Thanks

---

### Post by fabounet on 2009-12-11
the Cairo-Penguin applet has already several themes, just choose the one you want.

---

### Post by saltmore on 2009-12-11
> **ChappyHappy said:**
> Hi, where can I get a plug-in for another animal similar to the penguin?

There's a fish looking one at <http://www.cairo-dock.org/ww_page.php?p=Our%20Themes%20%28an%20overview%29>. The theme is called "Brit".

Thanks

Under accesories Cairo-Penguin. Configuration and then choose wanda theme.

---

### Post by ChappyHappy on 2009-12-12
Umm...I only have one theme available in the drop down list: "(Local) Classic".

Edit: I have all the cairo-dock files installed from synaptic except for the dev one.

---

### Post by fabounet on 2009-12-13
are you under a firewall or such thing ?
launch the dock in a terminal, and try to see some error message when it tries to connect to the server

---

### Post by ChappyHappy on 2009-12-16
> chappy@chappy-laptop:~$ cairo-dock
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
OpenGL renderer: Mesa DRI Intel(R) 965GM GEM 20090712 2009Q2 RC3 
warning :  (applet-gvfs.c:vfs_backend_list_directory:611)  
  gnome_integration : No such file or directory
WARNING: Application calling GLX 1.3 function "glXCreatePbuffer" when GLX 1.3 is not supported!  This is an application bug!
if your drivers are crappy, we'll know it immediately ...do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
 ok, they seem fine enough.
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/chappy/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
pRenderAttr->iMemorySize : 45
plus d'icone de cet ordre : 2
 -> on enleve un separateur
cd_sysmonitor_get_cpu_data: assertion `fTimeElapsed > 0.1' failed
 wget "http://themes.cairo-dock.org/gauges/Radium/Radium.tar.gz" -O "/tmp/cairo-dock-net-file.FNQ9dW" -t 2 -T 5
--2009-12-16 22:21:49--  [http://themes.cairo-dock.org/gauges/Radium/Radium.tar.gz](http://themes.cairo-dock.org/gauges/Radium/Radium.tar.gz)
Resolving themes.cairo-dock.org... failed: Connection timed out.
wget: unable to resolve host address `themes.cairo-dock.org'
warning :  (cairo-dock-themes-manager.c:cairo_dock_download_file:282)  
  an error occured while executing ' wget "http://themes.cairo-dock.org/gauges/Radium/Radium.tar.gz" -O "/tmp/cairo-dock-net-file.FNQ9dW" -t 2 -T 5'
warning :  (cairo-dock-themes-manager.c:cairo_dock_get_theme_path:1121)  
  couldn't retrieve distant theme Radium : couldn't get distant file Radium/Radium.tar.gz
 ====> cThemePath : (null)
gtk_widget_set: assertion `GTK_IS_WIDGET (widget)' failed
iNbConfigDialogs <- 1
cette batterie (BAT0) n'est pas presente.
warning :  (powermanager-dbus.c:dbus_connect_to_bus:138)  
  No battery were found
1 -> 1;-1
cairo_dock_refresh_launcher_gui ()

VERIFIER LE CHANGEMENT DE CONTAINER POUR TERMINAL

cairo_dock_refresh_launcher_gui ()
iNbConfigDialogs <- 0



I think I am, but I'm not entirely sure where I read that in the terminal. 
I dont have a firewall enabled though. All I did was get the gufw from synaptic but never ran it.

---

### Post by fabounet on 2009-12-17
oh, you're using an old version !
*wget *is broken in Karmic, so we have switched to *curl*.
so just install the 2.1.2 and enjoy ;-)

---

### Post by ChappyHappy on 2009-12-19
The one in the synaptic is version 2.0.9.
That would explain it. lol.

So after I upgrade using 'apt-get dist-upgrade', I should be able to change it from Pingu to something else?

---

### Post by ChappyHappy on 2009-12-19
Ok, I'm running 2.1.2 now.
But I still cant choose a theme.
At the bottom of the config window, it says "Could not get the list for Cairo-Penguin (no connection?)"

I am connected to the internet. And I dont believe I have any firewall running.

---

### Post by fabounet on 2009-12-20
maybe the connection timeout is too low for you ?
try to increase it in the "System" module (by default it's 5s)

---

### Post by omkardanke on 2010-02-10
How to increase the maximum download time of a theme to more than 300s? Because i have a really slow net connection. 400KB could take more than 5 mins.

---

### Post by fabounet on 2010-02-10
wow, really?
then just edit the file ~/.config/cairo-dock/current_theme/cairo-dock.conf, search for the key "conn max time" and set the value you want.

---

### Post by triva911 on 2010-08-07
How to change size of cairo-penguin ??

---

### Post by fabounet on 2010-08-10
the size is fixed.

---

