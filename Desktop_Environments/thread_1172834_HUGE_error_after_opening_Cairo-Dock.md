---
title: "HUGE error after opening Cairo-Dock"
date: 2009-05-29
forum: Desktop Environments
---

### Post by morbid_bean on 2009-05-29
Try to open cairo dock via applications>accessories> Cairo-dock and nothing happens

Try it in terminal:

```
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-nVidia.so' : (/usr/lib/cairo-dock/libcd-nVidia.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-clock.so' : (/usr/lib/cairo-dock/libcd-clock.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-logout.so' : (/usr/lib/cairo-dock/libcd-logout.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xmms.so' : (/usr/lib/cairo-dock/libcd-xmms.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Xgamma.so' : (/usr/lib/cairo-dock/libcd-Xgamma.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-dustbin.so' : (/usr/lib/cairo-dock/libcd-dustbin.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-rame.so' : (/usr/lib/cairo-dock/libcd-rame.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-quick-browser.so' : (/usr/lib/cairo-dock/libcd-quick-browser.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Animated-icons.so' : (/usr/lib/cairo-dock/libcd-Animated-icons.so: undefined symbol: myLabels)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-rhythmbox.so' : (/usr/lib/cairo-dock/libcd-rhythmbox.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-tomboy.so' : (/usr/lib/cairo-dock/libcd-tomboy.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-keyboard-indicator.so' : (/usr/lib/cairo-dock/libcd-keyboard-indicator.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-switcher.so' : (/usr/lib/cairo-dock/libcd-switcher.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-dialog-rendering.so' : (/usr/lib/cairo-dock/libcd-dialog-rendering.so: undefined symbol: myDialogs)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-stack.so' : (/usr/lib/cairo-dock/libcd-stack.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-motion_blur.so' : (/usr/lib/cairo-dock/libcd-motion_blur.so: undefined symbol: g_bUseOpenGL)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-terminal.so' : (/usr/lib/cairo-dock/libcd-terminal.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-icon-effect.so' : (/usr/lib/cairo-dock/libcd-icon-effect.so: undefined symbol: myLabels)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-systray.so' : (/usr/lib/cairo-dock/libcd-systray.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-drop_indicator.so' : (/usr/lib/cairo-dock/libcd-drop_indicator.so: undefined symbol: g_bUseOpenGL)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-AlsaMixer.so' : (/usr/lib/cairo-dock/libcd-AlsaMixer.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-wifi.so' : (/usr/lib/cairo-dock/libcd-wifi.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-powermanager.so' : (/usr/lib/cairo-dock/libcd-powermanager.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Cairo-Penguin.so' : (/usr/lib/cairo-dock/libcd-Cairo-Penguin.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-GMenu.so' : (/usr/lib/cairo-dock/libcd-GMenu.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-desklet-rendering.so' : (/usr/lib/cairo-dock/libcd-desklet-rendering.so: undefined symbol: myLabels)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-slider.so' : (/usr/lib/cairo-dock/libcd-slider.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Clipper.so' : (/usr/lib/cairo-dock/libcd-Clipper.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-weblets.so' : (/usr/lib/cairo-dock/libcd-weblets.so: undefined symbol: cairo_dock_pop_up_about_applet)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Dbus.so' : (/usr/lib/cairo-dock/libcd-Dbus.so: undefined symbol: myIcons)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-cpusage.so' : (/usr/lib/cairo-dock/libcd-cpusage.so: undefined symbol: cairo_dock_pop_up_about_applet)
*** glibc detected *** cairo-dock: free(): invalid pointer: 0xb707f18c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74b9604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb74bb5b6]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb7744126]
cairo-dock(cairo_dock_free_visit_card+0x20)[0x807d3f0]
cairo-dock[0x807e53b]
cairo-dock(cairo_dock_load_module+0x46)[0x8080186]
cairo-dock(cairo_dock_preload_module_from_directory+0xf1)[0x8080301]
cairo-dock(cairo_dock_initialize_module_manager+0x57)[0x80803c7]
cairo-dock(main+0x168b)[0x8063a1b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7460775]
cairo-dock[0x805e5b1]
======= Memory map: ========
08048000-080b5000 r-xp 00000000 08:06 83872      /usr/bin/cairo-dock
080b5000-080b6000 r--p 0006c000 08:06 83872      /usr/bin/cairo-dock
080b6000-080b7000 rw-p 0006d000 08:06 83872      /usr/bin/cairo-dock
080b7000-080b8000 rw-p 080b7000 00:00 0 
0814c000-081d0000 rw-p 0814c000 00:00 0          [heap]
b6c48000-b6c57000 r-xp 00000000 08:06 115036     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b6c57000-b6c58000 r--p 0000e000 08:06 115036     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b6c58000-b6c59000 rw-p 0000f000 08:06 115036     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b6c59000-b6c6b000 r-xp 00000000 08:06 83770      /usr/lib/libgvfscommon.so.0.0.0
b6c6b000-b6c6c000 r--p 00012000 08:06 83770      /usr/lib/libgvfscommon.so.0.0.0
b6c6c000-b6c6d000 rw-p 00013000 08:06 83770      /usr/lib/libgvfscommon.so.0.0.0
b6c6d000-b6c87000 r-xp 00000000 08:06 115037     /usr/lib/gio/modules/libgvfsdbus.so
b6c87000-b6c88000 r--p 00019000 08:06 115037     /usr/lib/gio/modules/libgvfsdbus.so
b6c88000-b6c89000 rw-p 0001a000 08:06 115037     /usr/lib/gio/modules/libgvfsdbus.so
b6d1e000-b6d21000 r-xp 00000000 08:06 572739     /lib/libuuid.so.1.2
b6d21000-b6d22000 r--p 00002000 08:06 572739     /lib/libuuid.so.1.2
b6d22000-b6d23000 rw-p 00003000 08:06 572739     /lib/libuuid.so.1.2
b6d23000-b6d2b000 r-xp 00000000 08:06 81826      /usr/lib/libdrm.so.2.4.0
b6d2b000-b6d2c000 r--p 00007000 08:06 81826      /usr/lib/libdrm.so.2.4.0
b6d2c000-b6d2d000 rw-p 00008000 08:06 81826      /usr/lib/libdrm.so.2.4.0
b6d2d000-b6d3a000 r-xp 00000000 08:06 572341     /lib/libgcc_s.so.1
b6d3a000-b6d3b000 r--p 0000c000 08:06 572341     /lib/libgcc_s.so.1
b6d3b000-b6d3c000 rw-p 0000d000 08:06 572341     /lib/libgcc_s.so.1
b6d3c000-b6e20000 r-xp 00000000 08:06 81867      /usr/lib/libstdc++.so.6.0.10
b6e20000-b6e24000 r--p 000e3000 08:06 81867      /usr/lib/libstdc++.so.6.0.10
b6e24000-b6e25000 rw-p 000e7000 08:06 81867      /usr/lib/libstdc++.so.6.0.10
b6e25000-b6e2b000 rw-p b6e25000 00:00 0 
b6e2b000-b6e36000 r-xp 00000000 08:06 83262      /usr/lib/libpangox-1.0.so.0.2400.1
b6e36000-b6e37000 r--p 0000a000 08:06 83262      /usr/lib/libpangox-1.0.so.0.2400.1
b6e37000-b6e38000 rw-p 0000b000 08:06 83262      /usr/lib/libpangox-1.0.so.0.2400.1
b6e38000-b6e4d000 r-xp 00000000 08:06 83310      /usr/lib/libICE.so.6.3.0
b6e4d000-b6e4e000 rw-p 00014000 08:06 83310      /usr/lib/libICE.so.6.3.0
b6e4e000-b6e50000 rw-p b6e4e000 00:00 0 
b6e50000-b6e57000 r-xp 00000000 08:06 81887      /usr/lib/libSM.so.6.0.0
b6e57000-b6e58000 r--p 00006000 08:06 81887      /usr/lib/libSM.so.6.0.0
b6e58000-b6e59000 rw-p 00007000 08:06 81887      /usr/lib/libSM.so.6.0.0
b6e59000-b6ea8000 r-xp 00000000 08:06 82019      /usr/lib/libXt.so.6.0.0
b6ea8000-b6ea9000 r--p 0004f000 08:06 82019      /usr/lib/libXt.so.6.0.0
b6ea9000-b6eac000 rw-p 00050000 08:06 82019      /usr/lib/libXt.so.6.0.0
b6eac000-b6ec1000 r-xp 00000000 08:06 83378      /usr/lib/libXmu.so.6.2.0
b6ec1000-b6ec2000 rw-p 00015000 08:06 83378      /usr/lib/libXmu.so.6.2.0
b6ec2000-b6f1a000 r-xp 00000000 08:06 82223      /usr/lib/libGL.so.1.2
b6f1a000-b6f1f000 r--p 00057000 08:06 82223      /usr/lib/libGL.so.1.2
b6f1f000-b6f24000 rwxp 0005c000 08:06 82223      /usr/lib/libGL.so.1.2
b6f24000-b6f25000 rwxp b6f24000 00:00 0 
b6f25000-b6f94000 r-xp 00000000 08:06 81777      /usr/lib/libGLU.so.1.3.070300
b6f94000-b6f95000 ---p 0006f000 08:06 81777      /usr/lib/libGLU.so.1.3.070300
b6f95000-b6f96000 r--p 0006f000 08:06 81777      /usr/lib/libGLU.so.1.3.070300
b6f96000-b6f97000 rw-p 00070000 08:06 81777      /usr/lib/libGLU.so.1.3.070300
b6f97000-b6fdf000 r-xp 00000000 08:06 83662      /usr/lib/libgdkglext-x11-1.0.so.0.0.0
b6fdf000-b6fe0000 r--p 00047000 08:06 83662      /usr/lib/libgdkglext-x11-1.0.so.0.0.0
b6fe0000-b6fe2000 rw-p 00048000 08:06 83662      /usr/lib/libgdkglext-x11-1.0.so.0.0.0
b6ff2000-b7012000 r-xp 00000000 08:06 114841     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7012000-b7013000 r--p 00020000 08:06 114841     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7013000-b7014000 rw-p 00021000 08:06 114841     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b7014000-b701b000 r-xp 00000000 08:06 82124      /usr/lib/libltdl.so.7.2.0
b701b000-b701c000 r--p 00006000 08:06 82124      /usr/lib/libltdl.so.7.2.0
b701c000-b701d000 rw-p 00007000 08:06 82124      /usr/lib/libltdl.so.7.2.0
b701d000-b7029000 r-xp 00000000 08:06 83291      /usr/lib/libtdb.so.1.1.3
b7029000-b702a000 r--p 0000b000 08:06 83291      /usr/lib/libtdb.so.1.1.3
b702a000-b702b000 rw-p 0000c000 08:06 83291      /usr/lib/libtdb.so.1.1.3
b702b000-b702f000 r-xp 00000000 08:06 84037      /usr/lib/libogg.so.0.5.3
b702f000-b7030000 r--p 00003000 08:06 84037      /usr/lib/libogg.so.0.5.3
b7030000-b7031000 rw-p 00004000 08:06 84037      /usr/lib/libogg.so.0.5.3
b7031000-b704c000 r-xp 00000000 08:06 84255      /usr/lib/libvorbis.so.0.4.0
b704c000-b704d000 r--p 0001a000 08:06 84255      /usr/lib/libvorbis.so.0.4.0
b704d000-b705b000 rw-p 0001b000 08:06 84255      /usr/lib/libvorbis.so.0.4.0
b705b000-b7062000 r-xp 00000000 08:06 84259      /usr/lib/libvorbisfile.so.3.2.0
b7062000-b7063000 r--p 00006000 08:06 84259      /usr/lib/libvorbisfile.so.3.2.0
b7063000-b7064000 rw-p 00007000 08:06 84259      /usr/lib/libvorbisfile.so.3.2.0
b7064000-b7071000 r-xp 00000000 08:06 84050      /usr/lib/libcanberra.so.0.1.4
b7071000-b7072000 r--p 0000d000 08:06 84050      /usr/lib/libcanberra.so.0.1.4
b7072000-b7073000 rw-p 0000e000 08:06 84050      /usr/lib/libcanberra.so.0.1.4
b7073000-b7077000 r-xp 00000000 08:06 83402      /usr/lib/libXxf86vm.so.1.0.0
b7077000-b7078000 r--p 00003000 08:06 83402      /usr/lib/libXxf86vm.so.1.0.0
b7078000-b7079000 rw-p 00004000 08:06 83402      /usr/lib/libXxf86vm.so.1.0.0
b7079000-b7081000 r-xp 00000000 08:06 149280     /usr/lib/cairo-dock/libcd-gnome-integration.so
b7081000-b7082000 r--p 00007000 08:06 149280     /usr/lib/cairo-dock/libcd-gnome-integration.so
b7082000-b7083000 rw-p 00008000 08:06 149280     /usr/lib/cairo-dock/libcd-gnome-integration.so
b7083000-b708d000 r-xp 00000000 08:06 589358     /lib/tls/i686/cmov/libnss_files-2.9.so
b708d000-b708e000 r--p 00009000 08:06 589358     /lib/tls/i686/cmov/libnss_files-2.9.so
b708e000-b708f000 rw-p 0000a000 08:06 589358     /lib/tls/i686/cmov/libnss_files-2.9.so
b708f000-b7098000 r-xp 00000000 08:06 589360     /lib/tls/i686/cmov/libnss_nis-2.9.so
b7098000-b7099000 r--p 00008000 08:06 589360     /lib/tls/i686/cmov/libnss_nis-2.9.so
b7099000-b709a000 rw-p 00009000 08:06 589360     /lib/tls/i686/cmov/libnss_nis-2.9.so
b709a000-b70af000 r-xp 00000000 08:06 589355     /lib/tls/i686/cmov/libnsl-2.9.so
b70af000-b70b0000 r--p 00014000 08:06 589355     /lib/tls/i686/cmov/libnsl-2.9.so
b70b0000-b70b1000 rw-p 00015000 08:06 589355     /lib/tls/i686/cmov/libnsl-2.9.so
b70b1000-b70b3000 rw-p b70b1000 00:00 0 
b70b3000-b70ba000 r-xp 00000000 08:06 589356     /lib/tls/i686/cmov/libnss_compat-2.9.so
b70ba000-b70bb000 r--p 00006000 08:06 589356     /lib/tls/i686/cmov/libnss_compat-2.9.so
b70bb000-b70bc000 rw-p 00007000 08:06 589356     /lib/tls/i686/cmov/libnss_compat-2.9.so
b70bc000-b70be000 r-xp 00000000 08:06 83838      /usr/lib/libgtkglext-x11-1.0.so.0.0.0
b70be000-b70bf000 r--p 00002000 08:06 83838      /usr/lib/libgtkglext-x11-1.0.so.0.0.0
b70bf000-b70c0000 rw-p 00003000 08:06 83838      /usr/lib/libgtkglext-x11-1.0.so.0.0.0
b70c0000-b70c1000 rw-p b70c0000 00:00 0 
b70c1000-b70c4000 r-xp 00000000 08:06 82093      /usr/lib/libcanberra-gtk.so.0.0.4
b70c4000-b70c5000 r--p 00002000 08:06 82093      /usr/lib/libcanberra-gtk.so.0.0.4
b70c5000-b70c6000 rw-p 00003000 08:06 82093      /usr/lib/libcanberra-gtk.so.0.0.4
b70c6000-b70ca000 r-xp 00000000 08:06 114844     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b70ca000-b70cb000 r--p 00003000 08:06 114844     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b70cb000-b70cc000 rw-p 00004000 08:06 114844     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b70cc000-b710b000 r--p 00000000 08:06 115262     /usr/lib/locale/en_US.utf8/LC_CTYPE
b710b000-b710c000 r--p 00000000 08:06 115429     /usr/lib/locale/en_US.uAborted
```

---

### Post by fabounet on 2009-05-29
see the wiki on cairo-dock.org for a step-by-step installation of this software.

---

