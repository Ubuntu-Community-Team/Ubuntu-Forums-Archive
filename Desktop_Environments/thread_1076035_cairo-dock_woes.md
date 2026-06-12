---
title: "cairo-dock woes"
date: 2009-02-20
forum: Desktop Environments
---

### Post by Pro$pect on 2009-02-20
I have the repsoitory setup for intrepid, ran apt-get to install cairo-dock and cairo-dock-plugins. There is no app launcher under any menus so I try running cairo through the terminal and this is what i'm getting:

cairo_dock_get_desklet_decoration (personnal)
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:1180)  
  Sorry but your X server does not support the extension.
 You can't have window thumbnails in the dock
  MaJ des decorations du fond -> 14.00x48.00
nouvelle icone d'appli (16777226)
iRotation:0°
decorations : default
 insertion de quitter apres GIMP Image Editor -> iSeparatorType : 3
iRotation:0°
decorations : default
cairo_dock_configure_desklet (246x609 ; (-529,-609) ; 0,0,0)
use size
on lance l'ecriture differee (13x13)
on lance l'ecriture differee (246x609)
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
iRotation:0°
on recupere les decorations personnelles au desklet
iRotation:0°
decorations : default
cairo_dock_configure_desklet (156x157 ; (-200,-157) ; 0,0,0)
use size
iRotation:0°
decorations : default
cairo_dock_configure_desklet (310x305 ; (-310,202) ; 0,0,0)
use size
on lance l'ecriture differee (13x13)
on lance l'ecriture differee (156x157)
on lance l'ecriture differee (13x13)
on lance l'ecriture differee (310x305)
iRotation:0°
decorations : default
iRotation:0°
decorations : default
  MaJ des decorations du fond -> 905.00x45.00
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
_cairo_dock_write_desklet_size (246x609 ; 246x609)
cairo_dock_get_desklet_decoration (dark)
cairo_dock_create_surface_from_image: assertion `rsvg_handle != NULL' failed
_cairo_dock_write_desklet_size (156x157 ; 156x157)
cairo_dock_get_desklet_decoration (dark)
_cairo_dock_write_desklet_size (310x305 ; 310x305)
cairo_dock_get_desklet_decoration (dark)
cairo_dock_create_surface_from_image: assertion `rsvg_handle != NULL' failed

The program runs but it is very out of wack and closes when I close the terminal. Would love to get this setup right because it looks amazing.

---

### Post by cityismine on 2009-02-21
I'm having the same problem, however I was able to lauch it by pressing alt+f2 and punching in "cairo-dock".

---

### Post by Pro$pect on 2009-02-21
yeah I can launch it that way but the program still doesn't run right, like say I launch firefox from the dock then the whole window border will turn red because there is an error. Even after killing cairo I will get red borders on anything I open as well.

---

