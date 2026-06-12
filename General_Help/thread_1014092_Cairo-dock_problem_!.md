---
title: "Cairo-dock problem !"
date: 2008-12-17
forum: General Help
---

### Post by turna on 2008-12-17
i want to run cairo dock and get some errrors.


```
pr200@pr200-laptop ~ $ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
cairo_dock_get_desklet_decoration (personnal)
nouvelle icone d'appli (20971523)
nouvelle icone d'appli (27263006)
nouvelle icone d'appli (48234695)
nouvelle icone d'appli (60817415)
nouvelle icone d'appli (60818531)
 insertion de Uçbirim apres Musique -> iSeparatorType : 1
iRotation:0°
decorations : default
 insertion de horloge apres Uçbirim -> iSeparatorType : 3
iRotation:0°
decorations : default
iRotation:0°
decorations : default
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  '/home/pr200/.cairo-dock/current_theme/launchers/trash-empty.png' dosyas&#305; aç&#305;lamad&#305;: No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  '/home/pr200/.cairo-dock/current_theme/launchers/trash-full.png' dosyas&#305; aç&#305;lamad&#305;: No such file or directory
warning :  (applet-init.c:_load_theme:72)  
  Attention : couldn't find images, this theme is not valid
  MaJ des decorations du fond -> 1526,00x35,00
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
add default
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
```









and here is "cairo-dock -l debug" result







```

pr200@pr200-laptop ~ $ cairo-dock -l debug
message :  (cairo-dock.c:main:435)  
  Compiled with Glitz (hardware acceleration support)n
message :  (cairo-dock-dock-manager.c:cairo_dock_initialize_dock_manager:59)  
  
message :  (cairo-dock-renderer-manager.c:cairo_dock_initialize_renderer_manager:172)  
  
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (default)
debug   :  (cairo-dock-X-utilities.c:cairo_dock_get_nb_viewports:373)  
  pVirtualScreenSizeBuffer : 5120x1600
message :  (cairo-dock.c:main:587)  
  environnement de bureau : 1
message :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:239)  
  cairo_dock_preload_module_from_directory (/usr/lib/cairo-dock)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Tree)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Caroussel)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Simple)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Controler)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_renderer:80)  
  cairo_dock_register_desklet_renderer (Mediaplayer)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_dialog_renderer:125)  
  cairo_dock_register_dialog_renderer (Text)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
message :  (cairo-dock-dock-factory.c:cairo_dock_create_new_dock:84)  
  cairo_dock_create_new_dock (_MainDock_)
message :  (cairo-dock-renderer-manager.c:cairo_dock_set_renderer:201)  
  cairo_dock_set_renderer ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_update_conf_file_with_modules_full:945)  
  cairo_dock_update_conf_file_with_modules_full (/home/pr200/.config/cairo-dock/current_theme/cairo-dock.conf ; 0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), Applets, modules_0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), Applets, modules_1)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), Applets, modules_2)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/pr200/.config/cairo-dock/current_theme/cairo-dock.conf)
message :  (cairo-dock-dock-manager.c:cairo_dock_deactivate_temporary_auto_hide:525)  
  
message :  (cairo-dock-config.c:cairo_dock_read_conf_file:703)  
  g_cMainDockDefaultRendererName <- 3D plane
message :  (cairo-dock-config.c:cairo_dock_read_conf_file:853)  
   utilisation du repertoire local /home/pr200/.config/cairo-dock/current_theme/icons
cairo_dock_get_desklet_decoration (personnal)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (personnal)
debug   :  (cairo-dock-emblem.c:cairo_dock_get_emblem_path:237)  
  
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (cairo-dock-config.c:cairo_dock_read_conf_file:1174)  
    g_fReflectSize : 14,00 pixels
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:625)  
    cairo_dock_update_dock_size (11 / 1280)
message :  (cairo-dock-dock-factory.c:cairo_dock_build_docks_tree_with_desktop_files:564)  
  cairo_dock_build_docks_tree_with_desktop_files (/home/pr200/.config/cairo-dock/current_theme/launchers)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01nautilus.desktop
 we will assume that its class is 'nautilus'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Dosya Taray&#305;c&#305;/nautilus
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (nautilus)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Firefox Web Browser/firefox
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (firefox)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01BitTorrent.desktop
 we will assume that its class is 'transmission-gtk'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + BitTorrent/transmission-gtk
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (transmission-gtk)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01bmp.desktop
 we will assume that its class is 'beep-media-player'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Musique/beep-media-player
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (beep-media-player)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Mozilla Thunderbird Mail/News/thunderbird-bin
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (thunderbird-bin)
message :  (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:367)  
  no class defined for the launcher 01gnome-terminal.desktop
 we will assume that its class is 'gnome-terminal'
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-launcher-factory.c:cairo_dock_create_icon_from_desktop_file:402)  
  + Uçbirim/gnome-terminal
message :  (cairo-dock-class-manager.c:cairo_dock_inhibate_class:255)  
  cairo_dock_inhibate_class (gnome-terminal)
nouvelle icone d'appli (20971523)
nouvelle icone d'appli (27263006)
nouvelle icone d'appli (48234695)
message :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:531)  
  recuperation de 'Ubuntu Forums - Post New Thread - Mozilla Firefox' (bIsHidden : 0)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:539)  
    res_name : Navigator(9e7d6f0); res_class : Firefox(a0107c0)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:528)  
  cairo_dock_create_surface_from_class (firefox)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:532)  
  bUseXIcon:0
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:541)  
    Firefox Web Browser
message :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:544)  
  Firefox Web Browser va fournir genereusement sa surface
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-class-manager.c:cairo_dock_add_appli_to_class:194)  
  cairo_dock_add_appli_to_class (firefox)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1145)  
  cairo_dock_insert_appli_in_dock (Ubuntu Forums - Post New Thread - Mozilla Firefox, 48234695)
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:304)  
  
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:328)  
  >>> Firefox Web Browser prendra un indicateur au prochain redraw ! (Xid : 48234695)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1150)  
   -> se fait inhiber
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:408)  
    cette fenetre est timide
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:408)  
    cette fenetre est timide
nouvelle icone d'appli (60817415)
message :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:531)  
  recuperation de 'Uçbirim' (bIsHidden : 0)
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:539)  
    res_name : gnome-terminal(a012fe8); res_class : Gnome-terminal(a007b30)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:528)  
  cairo_dock_create_surface_from_class (gnome-terminal)
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:532)  
  bUseXIcon:0
debug   :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:541)  
    Uçbirim
message :  (cairo-dock-class-manager.c:cairo_dock_create_surface_from_class:544)  
  Uçbirim va fournir genereusement sa surface
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-class-manager.c:cairo_dock_add_appli_to_class:194)  
  cairo_dock_add_appli_to_class (gnome-terminal)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1145)  
  cairo_dock_insert_appli_in_dock (Uçbirim, 60817415)
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:304)  
  
message :  (cairo-dock-class-manager.c:cairo_dock_prevent_inhibated_class:328)  
  >>> Uçbirim prendra un indicateur au prochain redraw ! (Xid : 60817415)
message :  (cairo-dock-applications-manager.c:cairo_dock_insert_appli_in_dock:1150)  
   -> se fait inhiber
debug   :  (cairo-dock-application-factory.c:cairo_dock_create_icon_from_xwindow:408)  
    cette fenetre est timide
message :  (cairo-dock-modules.c:cairo_dock_activate_module:450)  
  cairo_dock_activate_module (clock)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1003)  
  cairo_dock_instanciate_module (/home/pr200/.config/cairo-dock/current_theme/plug-ins/clock/clock.conf)
iRotation:0°
decorations : default
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:31)  
  cairo_dock_create_applet_surface (48,00x48,00 x 2,00 / 1)
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:40)  
   -> 40,00x40,00 x 2,00
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list (/home/pr200/.config/cairo-dock/current_theme/plug-ins/clock/clock.conf, Module, theme)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/pr200/.config/cairo-dock/current_theme/plug-ins/clock/clock.conf)
message :  (applet-init.c:init:82)  
  init (/home/pr200/.config/cairo-dock/current_theme/plug-ins/clock/clock.conf)

message :  (applet-init.c:_load_theme:40)  
  _load_theme (/usr/share/cairo-dock/plug-ins/clock/themes/radium)
debug   :  (applet-init.c:_load_back_and_fore_ground:64)  
  
debug   :  (applet-digital.c:cd_clock_configure_digital:22)  
  cd_clock_configure_digital
debug   :  (applet-digital.c:cd_clock_configure_digital:30)  
  Clock: Using /usr/share/cairo-dock/plug-ins/clock/digital/default/config digital theme
debug   :  (applet-digital.c:cd_clock_digital_load_frames:73)  
  cd_clock_digital_load_frames
debug   :  (applet-digital.c:cd_clock_digital_load_frames:81)  
  Clock: frame 1 width 10,00 (40,00 4)
debug   :  (applet-digital.c:cd_clock_digital_load_frames:90)  
  Clock: Loading /usr/share/cairo-dock/plug-ins/clock/digital/default/frame_0.svg frame (10,00x40,00)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (applet-digital.c:cd_clock_digital_load_frames:81)  
  Clock: frame 2 width 10,00 (40,00 4)
debug   :  (applet-digital.c:cd_clock_digital_load_frames:90)  
  Clock: Loading /usr/share/cairo-dock/plug-ins/clock/digital/default/frame_1.svg frame (10,00x40,00)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (applet-digital.c:cd_clock_digital_load_frames:81)  
  Clock: frame 3 width 10,00 (40,00 4)
debug   :  (applet-digital.c:cd_clock_digital_load_frames:90)  
  Clock: Loading /usr/share/cairo-dock/plug-ins/clock/digital/default/frame_2.svg frame (10,00x40,00)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
debug   :  (applet-digital.c:cd_clock_digital_load_frames:81)  
  Clock: frame 4 width 10,00 (40,00 4)
debug   :  (applet-digital.c:cd_clock_digital_load_frames:90)  
  Clock: Loading /usr/share/cairo-dock/plug-ins/clock/digital/default/frame_3.svg frame (10,00x40,00)
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
message :  (cairo-dock-dock-factory.c:cairo_dock_insert_icon_in_dock_full:717)  
  separateur necessaire
 insertion de horloge apres Musique -> iSeparatorType : 3
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (cairo-dock-modules.c:cairo_dock_activate_module:450)  
  cairo_dock_activate_module (rendering)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1003)  
  cairo_dock_instanciate_module (/home/pr200/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
message :  (rendering-init.c:init:120)  
  init (/home/pr200/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)

message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (Caroussel)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (3D plane)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (Parabolic)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (Rainbow)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (Slide)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (SimpleSlide)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_renderer:60)  
  cairo_dock_register_renderer (Curve)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (frame&reflects)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (scotch)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (frame with scotch)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (CD box)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (dark)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (clear)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (Starcraft2)
message :  (cairo-dock-renderer-manager.c:cairo_dock_register_desklet_decoration:150)  
  cairo_dock_register_desklet_decoration (none)
message :  (cairo-dock-renderer-manager.c:cairo_dock_set_renderer:201)  
  cairo_dock_set_renderer ((null))
debug   :  (rendering-3D-plane.c:cd_rendering_calculate_max_dock_size_3D_plane:39)  
  iMaxDockWidth <- 475; fInclinationOnHorizon <- 1,19; fExtraWidth <- 100,11
debug   :  (rendering-3D-plane.c:cd_rendering_calculate_max_dock_size_3D_plane:42)  
  pDock->iMaxDockWidth <- 575
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:625)  
    cairo_dock_update_dock_size (575 / 1280)
message :  (cairo-dock-modules.c:cairo_dock_activate_module:450)  
  cairo_dock_activate_module (logout)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1003)  
  cairo_dock_instanciate_module (/home/pr200/.config/cairo-dock/current_theme/plug-ins/logout/logout.conf)
iRotation:0°
decorations : default
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:31)  
  cairo_dock_create_applet_surface (32,00x32,00 x 2,00 / 1)
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:40)  
   -> 40,00x40,00 x 2,00
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
message :  (applet-init.c:init:13)  
  init (/home/pr200/.config/cairo-dock/current_theme/plug-ins/logout/logout.conf)

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 1;0;0
message :  (cairo-dock-modules.c:cairo_dock_activate_module:450)  
  cairo_dock_activate_module (dustbin)
message :  (cairo-dock-modules.c:cairo_dock_instanciate_module:1003)  
  cairo_dock_instanciate_module (/home/pr200/.config/cairo-dock/current_theme/plug-ins/dustbin/dustbin.conf)
iRotation:0°
decorations : default
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:31)  
  cairo_dock_create_applet_surface (32,00x32,00 x 2,00 / 1)
message :  (cairo-dock-applet-factory.c:cairo_dock_create_applet_surface:40)  
   -> 40,00x40,00 x 2,00
debug   :  (cairo-dock-load.c:cairo_dock_fill_one_icon_buffer:309)  
  cairo_dock_fill_one_icon_buffer () -> 40,00x40,00
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list (/home/pr200/.config/cairo-dock/current_theme/plug-ins/dustbin/dustbin.conf, Module, theme)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/pr200/.config/cairo-dock/current_theme/plug-ins/dustbin/dustbin.conf)
message :  (applet-init.c:init:76)  
  init (/home/pr200/.config/cairo-dock/current_theme/plug-ins/dustbin/dustbin.conf)

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:273)  
    on se base sur l'extension en desespoir de cause.
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  '/home/pr200/.cairo-dock/current_theme/launchers/trash-empty.png' dosyas&#305; aç&#305;lamad&#305;: No such file or directory
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:273)  
    on se base sur l'extension en desespoir de cause.
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  '/home/pr200/.cairo-dock/current_theme/launchers/trash-full.png' dosyas&#305; aç&#305;lamad&#305;: No such file or directory
message :  (applet-init.c:_load_theme:55)  
    /usr/share/cairo-dock/plug-ins/dustbin/themes/Metal/trashcan_full.png

message :  (applet-init.c:_load_theme:55)  
    /usr/share/cairo-dock/plug-ins/dustbin/themes/Metal/trashcan_empty.png

debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;1;0
warning :  (applet-init.c:_load_theme:72)  
  Attention : couldn't find images, this theme is not valid
message :  (applet-trashes-manager.c:cd_dustbin_add_one_dustbin:529)  
  cd_dustbin_add_one_dustbin (/home/pr200/.local/share/Trash/files)
message :  (applet-gvfs.c:vfs_backend_add_monitor:1082)  
  >>> moniteur ajoute sur /home/pr200/.local/share/Trash/files (a011fc8)
message :  (applet-trashes-manager.c:cd_dustbin_add_one_dustbin:540)  
    myConfig.iNbTrashes <- 0
message :  (applet-init.c:init:118)  
    0 dechet(s) actuellement (1)
message :  (applet-draw.c:cd_dustbin_draw_quick_info:143)  
  cd_dustbin_draw_quick_info (0)
debug   :  (cairo-dock-applet-facility.c:cairo_dock_set_quick_info:219)  
   cQuickInfo <- '(null)' (0x0)
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
debug   :  (cairo-dock-modules.c:cairo_dock_deactivate_module:508)  
  cairo_dock_deactivate_module ((null))
message :  (cairo-dock-renderer-manager.c:cairo_dock_set_renderer:201)  
  cairo_dock_set_renderer ((null))
debug   :  (rendering-3D-plane.c:cd_rendering_calculate_max_dock_size_3D_plane:39)  
  iMaxDockWidth <- 559; fInclinationOnHorizon <- 1,40; fExtraWidth <- 110,94
debug   :  (rendering-3D-plane.c:cd_rendering_calculate_max_dock_size_3D_plane:42)  
  pDock->iMaxDockWidth <- 670
debug   :  (cairo-dock-dock-factory.c:cairo_dock_update_dock_size:625)  
    cairo_dock_update_dock_size (670 / 1280)
debug   :  (cairo-dock-X-utilities.c:cairo_dock_set_strut_partial:182)  
  cairo_dock_set_strut_partial (0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
debug   :  (cairo-dock-X-utilities.c:cairo_dock_set_xwindow_type_hint:200)  
  cairo_dock_set_xwindow_type_hint (62914564, _NET_WM_WINDOW_TYPE_DOCK=376)
message :  (cairo-dock-dock-manager.c:cairo_dock_search_max_decorations_size:192)  
    decorations max : 670x37
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:267)  
    format : 0;0;0
debug   :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:273)  
    on se base sur l'extension en desespoir de cause.
  MaJ des decorations du fond -> 1340,00x37,00
debug   :  (cairo-dock-dock-factory.c:cairo_dock_place_root_dock:877)  
  cairo_dock_place_root_dock (1, 0, 1)
debug   :  (cairo-dock-dock-factory.c:cairo_dock_place_root_dock:890)  
   move to (128;775)
message :  (cairo-dock-desklet.c:cairo_dock_reload_desklets_decorations:1006)  
  cairo_dock_reload_desklets_decorations (0)
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
add default
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/pr200/.config/cairo-dock/current_theme/cairo-dock_easy.conf)
debug   :  (cairo-dock-modules.c:cairo_dock_update_conf_file_with_modules_full:945)  
  cairo_dock_update_conf_file_with_modules_full (/home/pr200/.config/cairo-dock/current_theme/cairo-dock_easy.conf ; 0)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), System, modules_0)

debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), System, modules_1)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_update_conf_file_with_list:227)  
  cairo_dock_update_conf_file_with_list ((null), System, modules_2)
debug   :  (cairo-dock-keyfile-utilities.c:cairo_dock_write_keys_to_file:18)  
  cairo_dock_write_keys_to_file (/home/pr200/.config/cairo-dock/current_theme/cairo-dock_easy.conf)
```

---

### Post by fabounet on 2008-12-18
these are just warnings, shouldn't pose a real problem.
isn't the dock working ?

---

### Post by turna on 2008-12-18
it is not working. at least i can not see any dock.

---

### Post by razy60 on 2008-12-18
applications-system tools should be in there.

Raz

---

### Post by fabounet on 2008-12-19
> i can not see any dock.
->
```
ps -ef | grep cairo
```
maybe it's hidden behind the gnome-panel ?

---

