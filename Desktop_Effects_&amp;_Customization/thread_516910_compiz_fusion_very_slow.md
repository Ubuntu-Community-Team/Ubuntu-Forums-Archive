---
title: "compiz fusion very slow"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by bowens44 on 2007-08-03
I am trying to get Compiz Fusion to work in an accepotable manner and not having much luck.

I have  an Athlon X2 3800
a geforce 7600 video card (using nvidia drivers)
2 gig of ram
Kubuntu 7.04

Beryl runs fine. In beryl everything  runs great. Very fast, With beryl running I get 7000 fps in glxgears.

Compiz fusion, moving or resizing windows is very jerky and slow, the only effects that seem to work are wobbly windows and the cube. Animations for minimizing etc don't seem to work after being set. All menus appear to open and close much more slowly then in Beryl.

In compiz fusion when I run glxgears I only get about 2500 fps.

I tried searching and haven't been successful in finding a solution.

Any help will be greatly appreciated.


my xorg.conf:
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "dbe"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Option "AddARGBGLXVisuals" "true"
    Option "DisableGLXRootClipping" "true"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by AndrewGene on 2007-08-03
Well it's not your card.  I'm on Ubuntu but i only run at about 500 fps and everything runs fast.

---

### Post by Scotty562 on 2007-08-03
Mine is in turtle mode as well. Intel Core two duo 2.0 ghz / Geforce 8400 gs about 2200 fps in glxgears.

---

### Post by yinglcs2 on 2007-08-03
I have a different experience.  
I used to use Beryl and then I switch to compiz fusion.
I notice the switching desktop effect in compiz fusion is much slower than Beryl.

Does anyone know this problem is fixed?

Thank you.

---

### Post by psyopper on 2007-08-03
If you are having slowdown in Compiz try disabling the "Fade Windows" plugin in CompizConfig Settings Manager.

Try making your launcher with the following command:
```
 export __GL_YIELD="NOTHING"; compiz --replace
```

If you are using Emerald  it should read
```
  export __GL_YIELD="NOTHING"; compiz --replace && emerald --replace
```

---

### Post by borovy3488 on 2007-08-11
I tried the above command and it didn't do anything.  Dont know what the deal is, but EVERYTHING is EXTREMELY slow.  Even as I am typing this, it is lagging.  Everything worked perfect in beryl.  Kinda sucks, I reallly wanted to go ahead and switch over.

---

### Post by mikibg on 2007-08-11
CF is crap...remove this alfa sh....
how 2 work with 80 plugin ???and now X11-xcb ....

---

### Post by ASPCartman on 2007-08-11
I have tis problem too. For exemple when i move my mouse pointer to up-left (while moving i also got mouse over menu buttons) expo starts... for 3 secs i have ~ 3 fps! WTF!? I WANT MY BERYL!:lolflag::mad:

---

### Post by Technoviking on 2007-08-18
> **psyopper said:**
> If you are having slowdown in Compiz try disabling the "Fade Windows" plugin in CompizConfig Settings Manager.

Try making your launcher with the following command:
```
 export __GL_YIELD="NOTHING"; compiz --replace
```

If you are using Emerald  it should read
```
  export __GL_YIELD="NOTHING"; compiz --replace && emerald --replace
```

The Fading Windows tip did wonders for me.

Mike

---

### Post by twothird on 2008-05-11
One of the reasons for slowdowns when rotating the cube, or when causing any other effects with compiz that use 3d graphics is because the graphic card (i got a 7600 GO) swaps from 2d mode to 3d mode. If, for instance, you start rotating the cube and it runs slow the first two seconds, and then starts running normally (easily noticable with 3d windows plugin), the problem might be happening because of the overload - not only do the windows need to be animated, the graphic processing method needs to be changed at the same time..
here's the solution [http://ubuntuforums.org/showpost.php?p=3873077&postcount=22](http://ubuntuforums.org/showpost.php?p=3873077&postcount=22)
this makes the graphic card run in 3d mode all the time.

---

