---
title: "I know this has been asked 100 times.. no buttons with compiz"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by BillGod on 2007-08-14
I had compiz working but not running a couple weeks ago.  I changed monitors now for some reason I cannot get it work  I have no buttons on anything and if you launch a new terminal you cannot even use it.

I have tried running 
compiz --replace 
compiz --replace --loose-binding -c emerald

beryl is 100% gone

i have these options added to my xorg.conf file.
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"

I have checked every thread and every site google returns on this issue.  Everything looks good.  here is my xorg.conf just in case someone see's a typo.  if you have any ideas on what else to try let me know.

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
EndSection

Section "Screen"

    Option "AddARGBGLXVisuals" "True"
    Option "DisableGLXRootClipping" "True"
   
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24

    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

EndSection




When I run from a terminal i get this..  i have to hit ctrl - c 3 times to break out of it.


me@bill-desktop:~$ compiz --replace --loose-binding -c emerald
Backend     : gconf
Integration : true
Profile     : default
Adding plugin resizeinfo (resizeinfo)
Adding plugin rotate (rotate)
Adding plugin 3d (3d)
Adding plugin winrules (winrules)
Adding plugin plane (plane)
Adding plugin opacify (opacify)
Adding plugin cube (cube)
Adding plugin wobbly (wobbly)
Adding plugin flash (flash)
Adding plugin annotate (annotate)
Adding plugin ezoom (ezoom)
Adding plugin video (video)
Adding plugin quickchange (quickchange)
Adding plugin ring (ring)
Adding plugin neg (neg)
Adding plugin fs (fs)
Adding plugin resize (resize)
Adding plugin colorfilter (colorfilter)
Adding plugin kiosk (kiosk)
Adding plugin water (water)
Adding plugin snap (snap)
Adding plugin thumbnail (thumbnail)
Adding plugin switcher (switcher)
Adding plugin screensaver (screensaver)
Adding plugin place (place)
Adding plugin decoration (decoration)
Adding plugin blur (blur)
Adding plugin screenshot (screenshot)
Adding plugin keybinding (keybinding)
Adding core settings (General Options)
Adding plugin shift (shift)
Adding plugin svg (svg)
Adding plugin mousegestures (mousegestures)
Adding plugin wallpaper (wallpaper)
Adding plugin vpswitch (vpswitch)
Adding plugin inotify (inotify)
Adding plugin glib (glib)
Adding plugin regex (regex)
Adding plugin zoom (zoom)
Adding plugin minimize (minimize)
Adding plugin cheatsheet (cheatsheet)
Adding plugin wall (wall)
Adding plugin expo (expo)
Adding plugin text (text)
Adding plugin visualevent (visualevent)
Adding plugin workarounds (workarounds)
Adding plugin dbus (dbus)
Adding plugin imgjpeg (imgjpeg)
Adding plugin move (move)
Adding plugin widget (widget)
Adding plugin put (put)
Adding plugin animation (animation)
Adding plugin cubecaps (cubecaps)
Adding plugin png (png)
Adding plugin notification (notification)
Adding plugin scale (scale)
Adding plugin scaleaddon (scaleaddon)
Adding plugin fade (fade)
Adding plugin clone (clone)
Adding plugin atlantis (atlantis)
Initializing core options...done
Initializing move options...done
Initializing resize options...done
Initializing 3d options...done
Initializing opacify options...done
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/compiz/default-cubecap.png
Initializing cube options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing switcher options...done
Initializing place options...done
Initializing zoom options...done
Initializing workarounds options...done
Initializing scale options...done
Initializing rotate options...done
/usr/bin/compiz: line 777:  7943 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


BillGod

---

### Post by Brezeck on 2007-08-14
I think your xorg.conf file has problem.

My suggestion:
remove your compiz fusion, graphic card driver and etc.
then, backup your xorg.conf file.
if you didn't do any backup, you could run "sudo dpkg-reconfigure xserver-xorg"  in terminal.
Then, i think you can log into Xserver correctly. Now, setup your xorg.conf files and setup your drivers, compiz fusion... etc.

---

### Post by conradlyn on 2007-08-14
maybe install a fusion-icon and launch it can help,at least,this thing did work on my system when i encountered with this damn problem.:guitar:

of course, after installing the fusion-icon, you have to change the window manager to compiz and window decorator to emerald,and with an emerald theme imported.

---

