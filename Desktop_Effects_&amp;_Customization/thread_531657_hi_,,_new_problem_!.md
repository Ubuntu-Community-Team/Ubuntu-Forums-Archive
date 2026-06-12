---
title: "hi ,, new problem !"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by mr.sms on 2007-08-21
hello every1

well ,, first of all i have a laptop ! HP pavilion 2097ea with nvidia GeForce Go 7200
i installed the driver from " ENVY "
then i tried 2 use compiz ! it worked but withe problem ! i can't minimize or maximize the windows or close it ! no botton :D
then i wrote in the terminal
sudo nvidia-xconfig --add-argb-glx-visuals -d 24 !
and everythins was perfect !!!

----

i installed compiz fusion ! well it works but with alot of problem
somtimes my windows turn 2 BLACK ! i can't see anything :(

[PHP]
smart@smart-laptop:~$ compiz --replaceBackend     : gconf
Integration : true
Profile     : default
Adding core settings (General Options)
Adding plugin cubereflex (cubereflex)
Adding plugin ring (ring)
Adding plugin gotovp (gotovp)
Adding plugin png (png)
Adding plugin extrawm (extrawm)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin wobbly (wobbly)
Adding plugin trailfocus (trailfocus)
Adding plugin scalefilter (scalefilter)
Adding plugin put (put)
Adding plugin scaleaddon (scaleaddon)
Adding plugin blur (blur)
Adding plugin regex (regex)
Adding plugin inotify (inotify)
Adding plugin screenshot (screenshot)
Adding plugin minimize (minimize)
Adding plugin opacify (opacify)
Adding plugin fadedesktop (fadedesktop)
Adding plugin water (water)
Adding plugin animation (animation)
Adding plugin decoration (decoration)
Adding plugin cube (cube)
Adding plugin fade (fade)
Adding plugin gears (gears)
Adding plugin vpswitch (vpswitch)
Adding plugin scale (scale)
Adding plugin thumbnail (thumbnail)
Adding plugin resize (resize)
Adding plugin firepaint (firepaint)
Adding plugin text (text)
Adding plugin wall (wall)
Adding plugin group (group)
Adding plugin dbus (dbus)
Adding plugin workarounds (workarounds)
Adding plugin splash (splash)
Adding plugin imgjpeg (imgjpeg)
Adding plugin winrules (winrules)
Adding plugin plane (plane)
Adding plugin showdesktop (showdesktop)
Adding plugin expo (expo)
Adding plugin ezoom (ezoom)
Adding plugin glib (glib)
Adding plugin rotate (rotate)
Adding plugin neg (neg)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin snap (snap)
Adding plugin clone (clone)
Adding plugin fs (fs)
Adding plugin crashhandler (crashhandler)
Adding plugin addhelper (addhelper)
Adding plugin place (place)
Adding plugin move (move)
Adding plugin bench (bench)
Adding plugin video (video)
Adding plugin zoom (zoom)
Adding plugin annotate (annotate)
Adding plugin resizeinfo (resizeinfo)
Initializing core options...done
Initializing svg options...done
Initializing screenshot options...done
Initializing water options...done
Initializing decoration options...done
Initializing resize options...done
Initializing firepaint options...done
Initializing workarounds options...done
Initializing imgjpeg options...done
Initializing place options...done
Initializing move options...done
Initializing zoom options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6087): Wnck-WARNING **: Unhandled action type (nil)
Initializing blur options...done
Initializing animation options...done
Initializing fade options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing cube options...done
Initializing scale options...done
Initializing rotate options...done
Initializing cubereflex options...done
Initializing switcher options...done


X connection to :0.0 broken (explicit kill or server shutdown).
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

[/PHP]

and when i start beryl ! the same thing happen again

[PHP]

smart@smart-laptop:~$ beryl-managersmart@smart-laptop:~$ **************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

X connection to :0.0 broken (explicit kill or server shutdown).
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"



[/PHP]

Can U help me please ?

---

### Post by mr.sms on 2007-08-22
up up  ,,, :(

---

