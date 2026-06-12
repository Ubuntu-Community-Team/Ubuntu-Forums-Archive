---
title: "Howto: Install Kiba Dock"
date: 2006-08-13
forum: Desktop Environments
---

### Post by scooper86 on 2006-08-13
I am writing this howto mainly so I can refer back to it cos my memory is not so good.

1. First install these packagse

sudo apt-get install libgtk2.0-dev libssl-dev build-essential cvs libgconf2-dev libgconf2-dev

2. Now download kiba dock from the cvs repository

cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock

3. Now move into the directory it has downloaded to

cd ./kiba-dock

4. Run the make command

make

5. Run the populate-dock.sh script

./populate-dock.sh

6. Now run kiba-dock

./dock

This should have all worked out nice and dandy and to make it autostart create a link to this file in your autostart folder located at /home/yourusername/.kde/Autostart/ and this will make it load at start up.

---

### Post by hellfried on 2006-08-16
> **scooper86 said:**
> I am writing this howto mainly so I can refer back to it cos my memory is not so good.

1. First install these packagse

sudo apt-get install libgtk2.0-dev libssl-dev build-essential cvs libgconf2-dev libgconf2-dev

2. Now download kiba dock from the cvs repository

cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock

3. Now move into the directory it has downloaded to

cd ./kiba-dock

4. Run the make command

make

5. Run the populate-dock.sh script

./populate-dock.sh

6. Now run kiba-dock

./dock

This should have all worked out nice and dandy and to make it autostart create a link to this file in your autostart folder located at /home/yourusername/.kde/Autostart/ and this will make it load at start up.

tried setting up kiba dock but ended up with a truckload of errors and no dock. i have compiz/xgl running on dapper.



hellfried@ubuntu:~$ cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cvs checkout: CVS password file /home/hellfried/.cvspass does not exist - creating a new file
cvs checkout: Updating kiba-dock
U kiba-dock/COPYING
U kiba-dock/Makefile
U kiba-dock/akamaru.c
U kiba-dock/akamaru.h
U kiba-dock/dock.c
U kiba-dock/index.html.in
U kiba-dock/kiba.schemas
U kiba-dock/log.sh
U kiba-dock/main.c
U kiba-dock/populate-dock.sh
hellfried@ubuntu:~$ cd ./kiba-dock
hellfried@ubuntu:~/kiba-dock$ make
cc -Wall -g -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -c -o akamaru.o akamaru.c
cc -Wall -g -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -c -o main.o main.c
cc -g  akamaru.o main.o  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lX11 -lgobject-2.0 -lcairo -lgconf-2 -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0   -o akamaru
cc -Wall -g -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -c -o dock.o dock.c
dock.c: In function ‘kiba_dock_replace_desktop_entry’:
dock.c:1020: warning: pointer targets in passing argument 3 of ‘g_file_get_contents’ differ in signedness
dock.c: In function ‘kiba_dock_drag_data_received’:
dock.c:2780: warning: pointer targets in passing argument 1 of ‘g_strrstr’ differ in signedness
dock.c:2781: warning: pointer targets in passing argument 1 of ‘g_strrstr’ differ in signedness
dock.c:2781: warning: pointer targets in assignment differ in signedness
dock.c:2783: warning: pointer targets in passing argument 1 of ‘strstr’ differ in signedness
dock.c:2791: warning: pointer targets in passing argument 1 of ‘strstr’ differ in signedness
cc -g  dock.o akamaru.o  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lX11 -lgobject-2.0 -lcairo -lgconf-2 -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0   -o dock
hellfried@ubuntu:~/kiba-dock$ ./populate-dock.sh
GCONF_CONFIG_SOURCE= \
                gconftool-2 --makefile-install-rule kiba.schemas
Attached schema `/schemas/apps/kiba/options/position' to key `/apps/kiba/options/position'
Installed schema `/schemas/apps/kiba/options/position' for locale `C'
Attached schema `/schemas/apps/kiba/options/elasticity' to key `/apps/kiba/options/elasticity'
Installed schema `/schemas/apps/kiba/options/elasticity' for locale `C'
Attached schema `/schemas/apps/kiba/options/gravity_multiplier' to key `/apps/kiba/options/gravity_multiplier'
Installed schema `/schemas/apps/kiba/options/gravity_multiplier' for locale `C'
Attached schema `/schemas/apps/kiba/options/throw_gravity' to key `/apps/kiba/options/throw_gravity'
Installed schema `/schemas/apps/kiba/options/throw_gravity' for locale `C'
Attached schema `/schemas/apps/kiba/options/model' to key `/apps/kiba/options/model'
Installed schema `/schemas/apps/kiba/options/model' for locale `C'
Attached schema `/schemas/apps/kiba/options/rope_launcher_distance' to key `/apps/kiba/options/rope_launcher_distance'
Installed schema `/schemas/apps/kiba/options/rope_launcher_distance' for locale `C'
Attached schema `/schemas/apps/kiba/options/rope_launcher_zooming' to key `/apps/kiba/options/rope_launcher_zooming'
Installed schema `/schemas/apps/kiba/options/rope_launcher_zooming' for locale `C'
Attached schema `/schemas/apps/kiba/options/rope_zoom_factor' to key `/apps/kiba/options/rope_zoom_factor'
Installed schema `/schemas/apps/kiba/options/rope_zoom_factor' for locale `C'
Attached schema `/schemas/apps/kiba/options/rope_gravity' to key `/apps/kiba/options/rope_gravity'
Installed schema `/schemas/apps/kiba/options/rope_gravity' for locale `C'
Attached schema `/schemas/apps/kiba/options/rope_spring_while_dragging' to key `/apps/kiba/options/rope_spring_while_dragging'
Installed schema `/schemas/apps/kiba/options/rope_spring_while_dragging' for locale `C'
Attached schema `/schemas/apps/kiba/options/bounce_height' to key `/apps/kiba/options/bounce_height'
Installed schema `/schemas/apps/kiba/options/bounce_height' for locale `C'
Attached schema `/schemas/apps/kiba/options/radius' to key `/apps/kiba/options/radius'
Installed schema `/schemas/apps/kiba/options/radius' for locale `C'
Attached schema `/schemas/apps/kiba/options/margin' to key `/apps/kiba/options/margin'
Installed schema `/schemas/apps/kiba/options/margin' for locale `C'
Attached schema `/schemas/apps/kiba/options/dock_color' to key `/apps/kiba/options/dock_color'
Installed schema `/schemas/apps/kiba/options/dock_color' for locale `C'
Attached schema `/schemas/apps/kiba/options/dock_alpha' to key `/apps/kiba/options/dock_alpha'
Installed schema `/schemas/apps/kiba/options/dock_alpha' for locale `C'
Attached schema `/schemas/apps/kiba/options/dock_border_color' to key `/apps/kiba/options/border_color'
Installed schema `/schemas/apps/kiba/options/dock_border_color' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_weight' to key `/apps/kiba/options/text_weight'
Installed schema `/schemas/apps/kiba/options/text_weight' for locale `C'
Attached schema `/schemas/apps/kiba/options/dock_border_alpha' to key `/apps/kiba/options/border_alpha'
Installed schema `/schemas/apps/kiba/options/dock_border_alpha' for locale `C'
Attached schema `/schemas/apps/kiba/options/border_width' to key `/apps/kiba/options/border_width'
Installed schema `/schemas/apps/kiba/options/border_width' for locale `C'
Attached schema `/schemas/apps/kiba/options/prelight_color' to key `/apps/kiba/options/prelight_color'
Installed schema `/schemas/apps/kiba/options/prelight_color' for locale `C'
Attached schema `/schemas/apps/kiba/options/prelight_alpha' to key `/apps/kiba/options/prelight_alpha'
Installed schema `/schemas/apps/kiba/options/prelight_alpha' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_type' to key `/apps/kiba/options/text_type'
Installed schema `/schemas/apps/kiba/options/text_type' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_size' to key `/apps/kiba/options/text_size'
Installed schema `/schemas/apps/kiba/options/text_size' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_color' to key `/apps/kiba/options/text_color'
Installed schema `/schemas/apps/kiba/options/text_color' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_alpha' to key `/apps/kiba/options/text_alpha'
Installed schema `/schemas/apps/kiba/options/text_alpha' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_bg_color' to key `/apps/kiba/options/text_bg_color'
Installed schema `/schemas/apps/kiba/options/text_bg_color' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_bg_alpha' to key `/apps/kiba/options/text_bg_alpha'
Installed schema `/schemas/apps/kiba/options/text_bg_alpha' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_border_color' to key `/apps/kiba/options/text_border_color'
Installed schema `/schemas/apps/kiba/options/text_border_color' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_border_alpha' to key `/apps/kiba/options/text_border_alpha'
Installed schema `/schemas/apps/kiba/options/text_border_alpha' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_icon_padding' to key `/apps/kiba/options/text_icon_padding'
Installed schema `/schemas/apps/kiba/options/text_icon_padding' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_border_width' to key `/apps/kiba/options/text_border_width'
Installed schema `/schemas/apps/kiba/options/text_border_width' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_enable' to key `/apps/kiba/options/text_enable'
Installed schema `/schemas/apps/kiba/options/text_enable' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_placement_x' to key `/apps/kiba/options/text_placement_x'
Installed schema `/schemas/apps/kiba/options/text_placement_x' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_placement_y' to key `/apps/kiba/options/text_placement_y'
Installed schema `/schemas/apps/kiba/options/text_placement_y' for locale `C'
Attached schema `/schemas/apps/kiba/options/border_style' to key `/apps/kiba/options/border_style'
Installed schema `/schemas/apps/kiba/options/border_style' for locale `C'
Attached schema `/schemas/apps/kiba/options/mouseover_bouncing' to key `/apps/kiba/options/mouseover_bouncing'
Installed schema `/schemas/apps/kiba/options/mouseover_bouncing' for locale `C'
Attached schema `/schemas/apps/kiba/options/mouseover_bouncing_height' to key `/apps/kiba/options/mouseover_bouncing_height'
Installed schema `/schemas/apps/kiba/options/mouseover_bouncing_height' for locale `C'
Attached schema `/schemas/apps/kiba/options/friction' to key `/apps/kiba/options/friction'
Installed schema `/schemas/apps/kiba/options/friction' for locale `C'
Attached schema `/schemas/apps/kiba/options/inertia' to key `/apps/kiba/options/inertia'
Installed schema `/schemas/apps/kiba/options/inertia' for locale `C'
Attached schema `/schemas/apps/kiba/options/icon_size' to key `/apps/kiba/options/icon_size'
Installed schema `/schemas/apps/kiba/options/icon_size' for locale `C'
Attached schema `/schemas/apps/kiba/options/k' to key `/apps/kiba/options/k'
Installed schema `/schemas/apps/kiba/options/k' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_hide_delay' to key `/apps/kiba/options/text_hide_delay'
Installed schema `/schemas/apps/kiba/options/text_hide_delay' for locale `C'
Attached schema `/schemas/apps/kiba/options/auto_hide_speed' to key `/apps/kiba/options/auto_hide_speed'
Installed schema `/schemas/apps/kiba/options/auto_hide_speed' for locale `C'
Attached schema `/schemas/apps/kiba/options/auto_hide_area' to key `/apps/kiba/options/auto_hide_area'
Installed schema `/schemas/apps/kiba/options/auto_hide_area' for locale `C'
Attached schema `/schemas/apps/kiba/options/text_while_dragging' to key `/apps/kiba/options/text_while_dragging'
Installed schema `/schemas/apps/kiba/options/text_while_dragging' for locale `C'
Attached schema `/schemas/apps/kiba/options/cap_size' to key `/apps/kiba/options/cap_size'
Installed schema `/schemas/apps/kiba/options/cap_size' for locale `C'
Attached schema `/schemas/apps/kiba/options/auto_hide' to key `/apps/kiba/options/auto_hide'
Installed schema `/schemas/apps/kiba/options/auto_hide' for locale `C'
Installed schema `/schemas/apps/kiba/launchers/file' for locale `C'
Installed schema `/schemas/apps/kiba/launchers/position' for locale `C'
hellfried@ubuntu:~/kiba-dock$ ./dock
Cant copy /usr/share/applications/gnome-file-roller.desktop to /home/hellfried/.kiba-dock/gnome-file-roller.desktop

** ERROR **: cant load file /home/hellfried/.kiba-dock/background.desktop into buffer notifications: PQR\x8bT$\u0010\x8bD$\u000c\xe8,
aborting...
Aborted

---

### Post by Lunar_Lamp on 2006-08-16
I get the same error when trying to run ./dock after a successful make.

```
$ ./dock
GTK Accessibility Module initialized
Cant copy /usr/share/applications/gnome-file-roller.desktop to /home/ed/.kiba-dock/gnome-file-roller.desktop
Cant copy /usr/share/applications/epiphany.desktop to /home/ed/.kiba-dock/epiphany.desktop

** ERROR **: cant load file /home/ed/.kiba-dock/background.desktop into buffer notifications: PQR\x8bT$\u0010\x8bD$\u000c\xe8,
aborting...
Aborted

```

---

### Post by Lunar_Lamp on 2006-08-16
However, it now works:

I ran ./akamura and played around a bit with the lines on screen, and then running ./dock worked

---

### Post by Lunar_Lamp on 2006-08-16
Too add launchers, you need to carefully drag icons on there from the applications menu (or existing launchers).  Wait until they have a litle black "plus" sign by them - when you release the mouse button to add it, the bar will crash, but when you re-run './dock' the icon will be there as desired.  To remove icons simple right click and say "remove launcher".

---

### Post by scooper86 on 2006-08-22
yea im pretty sure that bug is in the actual kiba dock itself if you keep checking the compiz forums they will tell you when new updates are available

---

### Post by hellfried on 2006-08-24
> **scooper86 said:**
>  

This should have all worked out nice and dandy and to make it autostart create a link to this file in your autostart folder located at /home/yourusername/.kde/Autostart/ and this will make it load at start up.

i don't see the Autostart folder in /.kde. do i have to create a new folder and put the dock link inside?
i also can't seem to delete unwanted launchers from the dock. when i right click on the icon it just opens up the program.

---

### Post by Lunar_Lamp on 2006-08-24
I think there is a file in ~/.kiba that you can edit.

Actually, each of the iles in that folder refers to an item on the dock, use "less FILE" to view te contents and work out what it's for, and then delete the unwanted files.

---

### Post by Big_J on 2006-08-27
I can't install...

>  sudo apt-get install libgtk2.0-dev libssl-dev build-essential cvs libgconf2-dev libgconf2-dev
Reading package lists... Done
Building dependency tree... Done
libssl-dev is already the newest version.
build-essential is already the newest version.
cvs is already the newest version.
libgconf2-dev is already the newest version.
libgconf2-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages


Any ideas?

---

### Post by TripleE on 2006-08-28
I have tried to install kiba, but I am getting some errors.  I have resolved 2 of them by installing libglitz-glx1-dev and libglade2-dev.  Now I am getting the following error and am not sure what the package for librsvg-2.0 is.  Any help?

Here is the first part of my error below.  There is a ton of errors from 143-769.

```
$ make
Package librsvg-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `librsvg-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'librsvg-2.0' found
cc -Wall -g   -c -o akamaru.o akamaru.c
akamaru.c:16:18: error: glib.h: No such file or directory
In file included from akamaru.c:22:
akamaru.h:143: error: syntax error before ‘gboolean’

```

---

### Post by general_error on 2006-09-02
Failled to compile for me:

```
root@jackal:/tmp# cd ./kiba-dock/
root@jackal:/tmp/kiba-dock# make
Package librsvg-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `librsvg-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'librsvg-2.0' found
Package glitz-glx was not found in the pkg-config search path.
Perhaps you should add the directory containing `glitz-glx.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glitz-glx' found
Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
cc -Wall -g   -c -o akamaru.o akamaru.c
akamaru.c:16:18: error: glib.h: No such file or directory
In file included from akamaru.c:22:
akamaru.h:143: error: syntax error before ‘gboolean’
akamaru.h:143: warning: no semicolon at end of struct or union
akamaru.h:145: warning: type defaults to ‘int’ in declaration of ‘animated_background’
akamaru.h:145: warning: data definition has no type or storage class
akamaru.h:146: error: syntax error before ‘animate_text’
akamaru.h:146: warning: type defaults to ‘int’ in declaration of ‘animate_text’
akamaru.h:146: warning: data definition has no type or storage class
akamaru.h:149: error: syntax error before ‘auto_hide’
akamaru.h:149: warning: type defaults to ‘int’ in declaration of ‘auto_hide’
akamaru.h:149: warning: data definition has no type or storage class
akamaru.h:154: error: syntax error before ‘*’ token
akamaru.h:154: warning: type defaults to ‘int’ in declaration of ‘border_color’
akamaru.h:154: warning: data definition has no type or storage class
akamaru.h:155: error: syntax error before ‘*’ token
akamaru.h:155: warning: type defaults to ‘int’ in declaration of ‘text_border_style’
akamaru.h:155: warning: data definition has no type or storage class
akamaru.h:163: error: syntax error before ‘*’ token
akamaru.h:163: warning: type defaults to ‘int’ in declaration of ‘dock_color_1’
akamaru.h:163: warning: data definition has no type or storage class
akamaru.h:164: error: syntax error before ‘*’ token
akamaru.h:164: warning: type defaults to ‘int’ in declaration of ‘dock_color_2’
akamaru.h:164: warning: data definition has no type or storage class
akamaru.h:165: error: syntax error before ‘*’ token
akamaru.h:165: warning: type defaults to ‘int’ in declaration of ‘dock_color_3’
akamaru.h:165: warning: data definition has no type or storage class
akamaru.h:166: error: syntax error before ‘*’ token
akamaru.h:166: warning: type defaults to ‘int’ in declaration of ‘dock_color_4’
akamaru.h:166: warning: data definition has no type or storage class
akamaru.h:167: error: syntax error before ‘*’ token
akamaru.h:167: warning: type defaults to ‘int’ in declaration of ‘dock_color_5’
akamaru.h:167: warning: data definition has no type or storage class
akamaru.h:169: error: syntax error before ‘*’ token
akamaru.h:169: warning: type defaults to ‘int’ in declaration of ‘dock_bg_png_file’
akamaru.h:169: warning: data definition has no type or storage class
akamaru.h:170: error: syntax error before ‘*’ token
akamaru.h:170: warning: type defaults to ‘int’ in declaration of ‘dock_bg_style’
akamaru.h:170: warning: data definition has no type or storage class
akamaru.h:171: error: syntax error before ‘*’ token
akamaru.h:171: warning: type defaults to ‘int’ in declaration of ‘dock_style’akamaru.h:171: warning: data definition has no type or storage class
akamaru.h:176: error: syntax error before ‘mouseover_bouncing’
akamaru.h:176: warning: type defaults to ‘int’ in declaration of ‘mouseover_bouncing’
akamaru.h:176: warning: data definition has no type or storage class
akamaru.h:177: error: syntax error before ‘launcher_zooming’
akamaru.h:177: warning: type defaults to ‘int’ in declaration of ‘launcher_zooming’
akamaru.h:177: warning: data definition has no type or storage class
akamaru.h:179: error: syntax error before ‘monitor_number’
akamaru.h:179: warning: type defaults to ‘int’ in declaration of ‘monitor_number’
akamaru.h:179: warning: data definition has no type or storage class
akamaru.h:182: error: syntax error before ‘*’ token
akamaru.h:182: warning: type defaults to ‘int’ in declaration of ‘prelight_color’
akamaru.h:182: warning: data definition has no type or storage class
akamaru.h:183: error: syntax error before ‘*’ token
akamaru.h:183: warning: type defaults to ‘int’ in declaration of ‘text_color’akamaru.h:183: warning: data definition has no type or storage class
akamaru.h:185: error: syntax error before ‘*’ token
akamaru.h:185: warning: type defaults to ‘int’ in declaration of ‘text_bg_style’
akamaru.h:185: warning: data definition has no type or storage class
akamaru.h:187: error: syntax error before ‘*’ token
akamaru.h:187: warning: type defaults to ‘int’ in declaration of ‘text_shadow_color’
akamaru.h:187: warning: data definition has no type or storage class
akamaru.h:189: error: syntax error before ‘*’ token
akamaru.h:189: warning: type defaults to ‘int’ in declaration of ‘text_bg_png_file’
akamaru.h:189: warning: data definition has no type or storage class
akamaru.h:190: error: syntax error before ‘*’ token
akamaru.h:190: warning: type defaults to ‘int’ in declaration of ‘text_bg_color_1’
akamaru.h:190: warning: data definition has no type or storage class
akamaru.h:191: error: syntax error before ‘*’ token
akamaru.h:191: warning: type defaults to ‘int’ in declaration of ‘text_bg_color_2’
akamaru.h:191: warning: data definition has no type or storage class
akamaru.h:192: error: syntax error before ‘*’ token
akamaru.h:192: warning: type defaults to ‘int’ in declaration of ‘text_bg_color_3’
akamaru.h:192: warning: data definition has no type or storage class
akamaru.h:193: error: syntax error before ‘*’ token
akamaru.h:193: warning: type defaults to ‘int’ in declaration of ‘text_bg_color_4’
akamaru.h:193: warning: data definition has no type or storage class
akamaru.h:194: error: syntax error before ‘*’ token
akamaru.h:194: warning: type defaults to ‘int’ in declaration of ‘text_bg_color_5’
akamaru.h:194: warning: data definition has no type or storage class
akamaru.h:200: error: syntax error before ‘*’ token
akamaru.h:200: warning: type defaults to ‘int’ in declaration of ‘text_border_color’
akamaru.h:200: warning: data definition has no type or storage class
akamaru.h:202: error: syntax error before ‘*’ token
akamaru.h:202: warning: type defaults to ‘int’ in declaration of ‘text_type’
akamaru.h:202: warning: data definition has no type or storage class
akamaru.h:205: error: syntax error before ‘text_enable’
akamaru.h:205: warning: type defaults to ‘int’ in declaration of ‘text_enable’
akamaru.h:205: warning: data definition has no type or storage class
akamaru.h:208: error: syntax error before ‘*’ token
akamaru.h:208: warning: type defaults to ‘int’ in declaration of ‘text_placement_x’
akamaru.h:208: warning: data definition has no type or storage class
akamaru.h:209: error: syntax error before ‘*’ token
akamaru.h:209: warning: type defaults to ‘int’ in declaration of ‘text_placement_y’
akamaru.h:209: warning: data definition has no type or storage class
akamaru.h:210: error: syntax error before ‘*’ token
akamaru.h:210: warning: type defaults to ‘int’ in declaration of ‘text_weight’
akamaru.h:210: warning: data definition has no type or storage class
akamaru.h:211: error: syntax error before ‘text_while_dragging’
akamaru.h:211: warning: type defaults to ‘int’ in declaration of ‘text_while_dragging’
akamaru.h:211: warning: data definition has no type or storage class
akamaru.h:217: error: syntax error before ‘launcher_e17_pulse’
akamaru.h:217: warning: type defaults to ‘int’ in declaration of ‘launcher_e17_pulse’
akamaru.h:217: warning: data definition has no type or storage class
akamaru.h:218: error: syntax error before ‘launcher_pulse’
akamaru.h:218: warning: type defaults to ‘int’ in declaration of ‘launcher_pulse’
akamaru.h:218: warning: data definition has no type or storage class
akamaru.h:219: error: syntax error before ‘launcher_pulse_exec’
akamaru.h:219: warning: type defaults to ‘int’ in declaration of ‘launcher_pulse_exec’
akamaru.h:219: warning: data definition has no type or storage class
akamaru.h:225: error: syntax error before ‘}’ token
akamaru.c: In function ‘model_add_spring’:
akamaru.c:98: warning: implicit declaration of function ‘g_new’
akamaru.c:98: error: syntax error before ‘Spring’
akamaru.c:102: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_delete_spring’:
akamaru.c:111: warning: implicit declaration of function ‘g_free’
akamaru.c: In function ‘model_for_each_spring’:
akamaru.c:117: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_add_stick’:
akamaru.c:133: error: syntax error before ‘Stick’
akamaru.c:137: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_stick’:
akamaru.c:145: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_add_string’:
akamaru.c:161: error: syntax error before ‘String’
akamaru.c:165: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_string’:
akamaru.c:180: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_add_offset_spring’:
akamaru.c:189: error: syntax error before ‘OffsetSpring’
akamaru.c:194: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_offset_spring’:
akamaru.c:202: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_add_spacer’:
akamaru.c:218: error: syntax error before ‘Spacer’
akamaru.c:222: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_spacer’:
akamaru.c:237: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_add_anchor’:
akamaru.c:253: error: syntax error before ‘Anchor’
akamaru.c:257: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_anchor’:
akamaru.c:272: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘polygon_init_from_va_list’:
akamaru.c:286: error: syntax error before ‘Point’
akamaru.c:294: error: syntax error before ‘Vector’
akamaru.c: In function ‘model_add_polygon’:
akamaru.c:323: warning: implicit declaration of function ‘g_new0’
akamaru.c:323: error: syntax error before ‘Polygon’
akamaru.c:327: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_polygon’:
akamaru.c:335: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_add_diamond’:
akamaru.c:341: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c:341: error: (Each undeclared identifier is reported only once
akamaru.c:341: error: for each function it appears in.)
akamaru.c: In function ‘model_add_rectangle’:
akamaru.c:352: error: ‘FALSE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_enclosing_rectangle’:
akamaru.c:359: error: ‘TRUE’ undeclared (first use in this function)
akamaru.c: In function ‘model_add_offset’:
akamaru.c:367: error: syntax error before ‘Offset’
akamaru.c:369: error: syntax error before ‘Object’
akamaru.c:372: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_offset’:
akamaru.c:380: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_init’:
akamaru.c:386: error: dereferencing pointer to incomplete type
akamaru.c:387: error: dereferencing pointer to incomplete type
akamaru.c:387: warning: implicit declaration of function ‘G_STRUCT_OFFSET’
akamaru.c:387: error: syntax error before ‘Object’
akamaru.c:388: error: dereferencing pointer to incomplete type
akamaru.c:388: error: syntax error before ‘Spacer’
akamaru.c:389: error: dereferencing pointer to incomplete type
akamaru.c:389: error: syntax error before ‘String’
akamaru.c:390: error: dereferencing pointer to incomplete type
akamaru.c:390: error: syntax error before ‘Stick’
akamaru.c:391: error: dereferencing pointer to incomplete type
akamaru.c:391: error: syntax error before ‘Spring’
akamaru.c:392: error: dereferencing pointer to incomplete type
akamaru.c:392: error: syntax error before ‘Anchor’
akamaru.c:393: error: dereferencing pointer to incomplete type
akamaru.c:393: error: syntax error before ‘Polygon’
akamaru.c:394: error: dereferencing pointer to incomplete type
akamaru.c:394: error: syntax error before ‘Offset’
akamaru.c:395: error: dereferencing pointer to incomplete type
akamaru.c:396: error: syntax error before ‘OffsetSpring’
akamaru.c: In function ‘model_add_object’:
akamaru.c:404: error: syntax error before ‘Object’
akamaru.c:410: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_for_each_object’:
akamaru.c:426: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_delete_spacers’:
akamaru.c:438: error: dereferencing pointer to incomplete type
akamaru.c:439: error: dereferencing pointer to incomplete type
akamaru.c:439: error: syntax error before ‘Spacer’
akamaru.c: In function ‘model_fini’:
akamaru.c:460: error: dereferencing pointer to incomplete type
akamaru.c:461: error: dereferencing pointer to incomplete type
akamaru.c:462: error: dereferencing pointer to incomplete type
akamaru.c:463: error: dereferencing pointer to incomplete type
akamaru.c:464: error: dereferencing pointer to incomplete type
akamaru.c:465: error: dereferencing pointer to incomplete type
akamaru.c:468: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘object_accumulate_forces’:
akamaru.c:478: error: dereferencing pointer to incomplete type
akamaru.c:479: error: dereferencing pointer to incomplete type
akamaru.c:485: error: dereferencing pointer to incomplete type
akamaru.c:487: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘spring_accumulate_forces’:
akamaru.c:505: error: dereferencing pointer to incomplete type
akamaru.c:506: error: dereferencing pointer to incomplete type
akamaru.c:507: error: dereferencing pointer to incomplete type
akamaru.c:508: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘offset_spring_accumulate_forces’:
akamaru.c:524: error: dereferencing pointer to incomplete type
akamaru.c:525: error: dereferencing pointer to incomplete type
akamaru.c:526: error: dereferencing pointer to incomplete type
akamaru.c:527: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘object_constrain_polygon’:
akamaru.c:639: error: dereferencing pointer to incomplete type
akamaru.c: In function ‘model_step’:
akamaru.c:766: error: dereferencing pointer to incomplete type
akamaru.c:769: error: dereferencing pointer to incomplete type
make: *** [akamaru.o] Error 1

```

---

### Post by ayoli on 2006-09-02
looks like you forget ./configure before make, and you may apt-get some devel packages (ie: libgtk2.0-dev and some more that configure output will tell to you).

---

### Post by shat on 2006-09-07
I used a similar method for my kiba-dock.

I had to use aptitude to get the dependencies all correct, because the -dev versions that it required wanted some downgrading of packages I installed.  Aptitude handled it, but I had a problem with gnome-terminal and the new transparency.  I had to revert back to old gnome-terminal-with-fake-transparency.  Anyway, it was worth it for this app.  I was in love with the non-bordered-text-any fluff version, so I took most of it off.

---

### Post by montechristos on 2006-09-08
general_error try this 
[COLOR="Red"]sudo aptitude install build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev libglade2-dev[/COLOR]
and then
```
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cd kiba-dock/
./populate-dock.sh
make
```

Please look my problem.
When i type in my console ./kiba-dock/kiba-dock to run the aplication
it appears this message 
** Message: Cant copy /usr/share/applications/epiphany.desktop to /home/christos/.kiba-dock/epiphany.desktop

The kiba-dock it appears, i can move it left, right ,up, down but i can't click the icons.
When i try to click them they become black.
Please [IMG]http://i64.photobucket.com/albums/h170/Montechristos_awmn/Emoticons/pomocy.gif[/IMG]

---

### Post by Thought_Criminal on 2006-09-13
> **general_error said:**
> Failled to compile for me:

I get the same error as you do.
Sucks to be us.

---

### Post by argash on 2006-09-15
I'm not having any luck connecting to the cvs. are there any mirrors i could try? I havent had any luck finding a tarball either

---

### Post by one_stinky_bum on 2006-09-16
any help with svg support in cairo? Kiba keeps complaining that if you want to use svg, you've got to have svg support in cairo.

BTW, CVS worked fine here. I'm on Dapper.

---

### Post by FedeXX on 2006-09-18
How can i dock the kde menu button?

---

### Post by pau on 2006-09-28
Help! After a successful ./configure I get

```
melanos| make                                                                                                                  
make[1]: Entering directory `/home/pau/kiba-dock'
cd . && autoheader
make[1]: Leaving directory `/home/pau/kiba-dock'
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=[config.h] \
             /bin/sh ./config.status
config.status: creating [config.h]
config.status: error: cannot find input file: [config.h].in
make: *** [stamp-h] Error 1
```

But config.h and config.h.in are there :confused:

---

### Post by Moisteh on 2006-10-04
I've been trying to run kiba dock for teh past few days, with no luck.  

I keep getting this error, after make.

```
 
***@***-desktop:~/kiba-dock$ make
make[1]: Entering directory `/home/ian/kiba-dock'
cd . && autoheader
make[1]: Leaving directory `/home/ian/kiba-dock'
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=[config.h] \
             /bin/sh ./config.status
config.status: creating [config.h]
config.status: error: cannot find input file: [config.h].in
make: *** [stamp-h] Error 1
***@***-desktop:~/kiba-dock$

```

and i checked, and YES, config.h.in IS in the kiba-dock directory.

](*,)

---

