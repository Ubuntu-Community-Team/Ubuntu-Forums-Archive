---
title: "Cairo-Dock 1.6.3.1 problem - can't install plugins .deb file"
date: 2009-03-08
forum: Desktop Environments
---

### Post by dpcole72 on 2009-03-08
Hello.  I am new to Ubuntu, am somewhat computer savvy, but am running into a problem when installing Cairo-Dock's plugins.  (Currently, for the display modes it offers, there is no 3D mode; the plugins resolving that...)

When running the Synaptic Package file, I get this:

[i]error processing cairo-dock-plug-ins-v1.6.3.1_i686.deb (--install):
trying to overwrite '/usr/lib/cairo-dock/libcd-slider.so', which is also in package cairo-dock-plugins[/i]

I looked for "cairo-dock-plugins" in the Synaptic Package Manager, and it is not found.  Why is it claiming a duplicate file in a package that doesn't exist... exist?

Would I be brave or stupid to rename that folder then re-run the package file?

Any help would be much appreciated.

Thanks!

---

### Post by dpcole72 on 2009-03-08
Oops, sorry to bug you.  I figured out how to use the command line to remove said package.  Weird how it did not show up in the GUI package manager...  :)

> **dpcole72 said:**
> Hello.  I am new to Ubuntu, am somewhat computer savvy, but am running into a problem when installing Cairo-Dock's plugins.  (Currently, for the display modes it offers, there is no 3D mode; the plugins resolving that...)

When running the Synaptic Package file, I get this:

[i]error processing cairo-dock-plug-ins-v1.6.3.1_i686.deb (--install):
trying to overwrite '/usr/lib/cairo-dock/libcd-slider.so', which is also in package cairo-dock-plugins[/i]

I looked for "cairo-dock-plugins" in the Synaptic Package Manager, and it is not found.  Why is it claiming a duplicate file in a package that doesn't exist... exist?

Would I be brave or stupid to rename that folder then re-run the package file?

Any help would be much appreciated.

Thanks!

---

### Post by dpcole72 on 2009-03-08
Update - I rebooted my system and; all the plugins were gone.  I reinstalled the package, the reinstall did not fail, but after re-starting Cairo-Dock none of the accessories or functions has returned.  :(

Here is a copy of the error, can ayone help?

[i]  while opening module '/usr/lib/cairo-dock/libcd-rhythmbox.so' : (/usr/lib/cairo-dock/libcd-rhythmbox.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Dbus.so' : (/usr/lib/cairo-dock/libcd-Dbus.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Xgamma.so' : (/usr/lib/cairo-dock/libcd-Xgamma.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xmms.so' : (/usr/lib/cairo-dock/libcd-xmms.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-showDesklets.so' : (/usr/lib/cairo-dock/libcd-showDesklets.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-clock.so' : (/usr/lib/cairo-dock/libcd-clock.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-stack.so' : (/usr/lib/cairo-dock/libcd-stack.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-compiz-icon.so' : (/usr/lib/cairo-dock/libcd-compiz-icon.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-weather.so' : (/usr/lib/cairo-dock/libcd-weather.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-cpusage.so' : (/usr/lib/cairo-dock/libcd-cpusage.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-GMenu.so' : (/usr/lib/cairo-dock/libcd-GMenu.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-wifi.so' : (/usr/lib/cairo-dock/libcd-wifi.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-tomboy.so' : (/usr/lib/cairo-dock/libcd-tomboy.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (/usr/lib/cairo-dock/libcd-xfce-integration.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-showDesktop.so' : (/usr/lib/cairo-dock/libcd-showDesktop.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-terminal.so' : (/usr/lib/cairo-dock/libcd-terminal.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-slider.so' : (/usr/lib/cairo-dock/libcd-slider.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-rendering.so' : (/usr/lib/cairo-dock/libcd-rendering.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-systray.so' : (/usr/lib/cairo-dock/libcd-systray.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-AlsaMixer.so' : (/usr/lib/cairo-dock/libcd-AlsaMixer.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-switcher.so' : (/usr/lib/cairo-dock/libcd-switcher.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-gnome-integration-old.so' : (/usr/lib/cairo-dock/libcd-gnome-integration-old.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-rame.so' : (/usr/lib/cairo-dock/libcd-rame.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-netspeed.so' : (/usr/lib/cairo-dock/libcd-netspeed.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-gnome-integration.so' : (/usr/lib/cairo-dock/libcd-gnome-integration.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-powermanager.so' : (/usr/lib/cairo-dock/libcd-powermanager.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Clipper.so' : (/usr/lib/cairo-dock/libcd-Clipper.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-nVidia.so' : (/usr/lib/cairo-dock/libcd-nVidia.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-logout.so' : (/usr/lib/cairo-dock/libcd-logout.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-Cairo-Penguin.so' : (/usr/lib/cairo-dock/libcd-Cairo-Penguin.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-dustbin.so' : (/usr/lib/cairo-dock/libcd-dustbin.so: wrong ELF class: ELFCLASS32)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-shortcuts.so' : (/usr/lib/cairo-dock/libcd-shortcuts.so: wrong ELF class: ELFCLASS32)
cairo_dock_get_desklet_decoration (personnal)
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:1180)  
  Sorry but your X server does not support the extension.
 You can't have window thumbnails in the dock
  MaJ des decorations du fond -> 16.00x4.00
nouvelle icone d'appli (18874371)
nouvelle icone d'appli (29360160)
nouvelle icone d'appli (25165834)
nouvelle icone d'appli (56623116)
 insertion de Package Installer - cairo-dock-plug-ins apres Sun xVM VirtualBox -> iSeparatorType : 1
nouvelle icone d'appli (54526302)
nouvelle icone d'appli (54526430)
nouvelle icone d'appli (54526442)
nouvelle icone d'appli (25166218)
  MaJ des decorations du fond -> 1710.00x52.00
add personnal
add default
add personnal

[/i]

---

