---
title: "Going to install nVidia card, using ATI-- help"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by herbster on 2007-04-04
I currently have a Radeon 9700 Pro with fglrx drivers installed and am using an XGL+Beryl session, all has worked great, but my card is fried, so I am buying an nVidia card today and want to be clear on exactly what to do with respect to drivers.

Obviously, I install nVidia drivers (btw, anyone got a URL or just go to their site?), but do I **install nVidia drivers with fglrx still on my system OR do I UNINSTALL fglrx FIRST, and THEN install nVidia's drivers???**

Thanks!!

---

### Post by rabid9797 on 2007-04-04
fglrx is for ATI drivers only, you will need to uninstall and then reinstall with the nvidia drivers. the easiest way to do this is to:

1. uninstall fglrx
2. install your nvidia card
3. start up in recovery mode(or without X since it won't work anyway)
4. install nvidia drivers
```
sudo apt-get install nvidia-glx
```
5. reconfigure xorg.conf
 - there are two wasy to do this:
 1. (using the automatic way)
```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```
 2. or doing it manually by editing /etc/X11/xorg.conf and under "Device" replacing
```

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "ati"

```
with
```

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"

```

and then adding
```

Option "AddARGBGLXVisuals" "True"

```
to the end of the "Device" section and then at the very of the file xorg.conf file adding:
```

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

### Post by rabid9797 on 2007-04-04
oh, forgot to add, you'll need to use nano if you decide to edit xorg.conf manually

---

