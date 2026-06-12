---
title: "Need help in setting up compiz fusion"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by yinglcs2 on 2007-08-04
Hi,

I am trying to follow this thread in setting up compiz fusion on my ubuntu system:
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

When I run 'ompiz --replace', I get this error:

$compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Can you please tell me what am I missing?
Thank you.

---

### Post by yinglcs2 on 2007-08-04
After installing XGL, I am getting a new error:

```
 compiz --replace
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Backend     : ini
Integration : true
Profile     : default
Adding plugin reflex (reflex)
Adding plugin water (water)
Adding plugin scalefilter (scalefilter)
Adding plugin crashhandler (crashhandler)
Adding plugin fakeargb (fakeargb)
Adding plugin mousegestures (mousegestures)
Adding plugin cheatsheet (cheatsheet)
Adding plugin flash (flash)
Adding plugin cubereflex (cubereflex)
Adding plugin ring (ring)
Adding plugin zoom (zoom)
Adding plugin fade (fade)
Adding plugin snap (snap)
Adding plugin ezoom (ezoom)
Adding plugin cubecaps (cubecaps)
Adding plugin switcher (switcher)
Adding plugin firepaint (firepaint)
Adding plugin wall (wall)
Adding plugin text (text)
Adding plugin resize (resize)
Adding plugin thumbnail (thumbnail)
Adding plugin dbus (dbus)
Adding plugin colorfilter (colorfilter)
Adding plugin gears (gears)
Adding plugin animation (animation)
Adding core settings (General Options)
Adding plugin bench (bench)
Adding plugin cube (cube)
Adding plugin kiosk (kiosk)
Adding plugin fadedesktop (fadedesktop)
Adding plugin splash (splash)
Adding plugin neg (neg)
Adding plugin video (video)
Adding plugin decoration (decoration)
Adding plugin mblur (mblur)
Adding plugin notification (notification)
Adding plugin vpswitch (vpswitch)
Adding plugin gotovp (gotovp)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin addhelper (addhelper)
Adding plugin png (png)
Adding plugin inotify (inotify)
Adding plugin place (place)
Adding plugin quickchange (quickchange)
Adding plugin plane (plane)
Adding plugin 3d (3d)
Adding plugin fs (fs)
Adding plugin minimize (minimize)
Adding plugin opacify (opacify)
Adding plugin imgjpeg (imgjpeg)
Adding plugin regex (regex)
Adding plugin trailfocus (trailfocus)
Adding plugin wallpaper (wallpaper)
Adding plugin put (put)
Adding plugin annotate (annotate)
Adding plugin group (group)
Adding plugin rotate (rotate)
Adding plugin keybinding (keybinding)
Adding plugin atlantis (atlantis)
Adding plugin wobbly (wobbly)
Adding plugin blur (blur)
Adding plugin screensaver (screensaver)
Adding plugin showdesktop (showdesktop)
Adding plugin extrawm (extrawm)
Adding plugin tile (tile)
Adding plugin shift (shift)
Adding plugin visualevent (visualevent)
Adding plugin widget (widget)
Adding plugin scaleaddon (scaleaddon)
Adding plugin move (move)
Adding plugin clone (clone)
Adding plugin svg (svg)
Adding plugin snow (snow)
Adding plugin winrules (winrules)
Adding plugin glib (glib)
Adding plugin expo (expo)
Adding plugin resizeinfo (resizeinfo)
Adding plugin workarounds (workarounds)
Initializing core options...done
Initializing zoom options...done
Initializing resize options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing decoration options...done
Initializing place options...done
Initializing minimize options...done
Initializing wobbly options...done
Initializing move options...done
Initializing workarounds options...done
Initializing fade options...done
Initializing cube options...done
Initializing scale options...done
Initializing rotate options...done
Initializing switcher options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

```

---

### Post by yinglcs2 on 2007-08-04
Hi, 

I am able to get it to work with borders by doing this:

compiz --replace -c emerald &

I see the borders in the windows. But when I go to emerald setting manager and select another theme, it does not change the theme.

Can you please tell me how to switch theme in emerald when use with compiz fusion?

Thank you.

---

### Post by atomkarinca on 2007-08-04
i think you should have compiz fusion icon. you can start it with
```
fusion-icon
```
right-click the icon and select emerald for window decorator. then the changes will take effect.

---

### Post by dougfractal on 2007-08-17
hi yinglcs2 
i'm trying to collect specs on peoples 3D card setup, so I can help others out., I know you have an ati card. Can you send more info


**system spec grabber**

paste this in terminal
```
mkdir ~/Xinfo
cd ~/Xinfo
echo 'touch X.info # create file
lsb_release -d > X.info # version
uname -r >> X.info # kernel
lspci -nn >> X.info # list hardware
glxinfo | head -4 >> X.info
script -c " glxgears &  sleep 11 ;  pkill -15 glxgears"   
cat typescript | grep FPS >> X.info
cp /etc/X11/xorg.conf ./   # graphics file
cp /var/log/Xorg.0.log ./
cp /etc/modprobe.d/blacklist ./
aptitude search ~imesa ~ixorg  ~idbus ~icompiz -F "%20p %10v %10V %20d" > installed.txt
tar -czf xinfo.tar.gz X.info xorg.conf Xorg.0.log installed.txt blacklist ' | tee xinfo.sh
sed -i '1i#!/bin/bash' xinfo.sh
chmod a+x xinfo.sh
./xinfo.sh
echo -e "\nplease attach $PWD/**xinfo.tar.gz**"

```
please attach **xinfo.tar.gz**

---

