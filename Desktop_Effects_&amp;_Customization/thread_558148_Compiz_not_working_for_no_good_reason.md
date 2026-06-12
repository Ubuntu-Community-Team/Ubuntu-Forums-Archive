---
title: "Compiz not working for no good reason"
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by Ndyanabo on 2007-09-23
Hi, another noob trying to set up Compiz in Feisty. I've been trying all weekend to get it to work. Looked at all the Howtos, nothing doing.

My card: nVidia Geforce4 Ti 4400

installed the legacy driver with Envy. Seems to work fine. Glxgears works:

```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 Ti 4400/AGP/SSE2
OpenGL version string: 1.5.3 NVIDIA 71.85
...

```

Tried a lot of howtos to set up Compiz, most recently [Forlongs guide]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty").  

Basically, when I do run application  "compiz --replace", the screen blinks a bit, and then nothing happens. Restarting x, rebooting the computer, nothing happens. Compiz appears not to be working.

Anything obvious I'm missing?

thanks!

Here's my xorg.conf
```

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
    Option         "XkbOptions" "lv3:ralt_switch"
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
    Identifier     "GeForce4 Ti 4400 "
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce4 Ti 4400 "
    Monitor        "Generic Monitor"
    Option 	   "ARGBGLXVisuals" "True"
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
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

---

### Post by Forlong on 2007-09-23
> **Ndyanabo said:**
> Here's my xorg.conf
```
Option         "Composite" "Disable"
```
This needs to be set to **"Enable"**

---

### Post by Ndyanabo on 2007-09-23
OK, I made the correction, but had the exact same result.

by the way, thanks very much for your efforts, Forlong, here and in many other threads.

---

### Post by Forlong on 2007-09-24
Please post the output of ```
compiz --replace
```
in the terminal.

---

### Post by Ndyanabo on 2007-09-24
```
$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by Forlong on 2007-09-24
> **Ndyanabo said:**
> ```
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present.
```
Whoa, there's something seriously wrong, when it already segfults at this point.

What's the output of
```
glxinfo | grep GLX_EXT_texture_from_pixmap
```

---

### Post by Ndyanabo on 2007-09-24
```
$ glxinfo | grep GLX_EXT_texture_from_pixmap
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

---

### Post by petit.padavoine on 2007-09-24
Here is some little info on how to modify your xorg.conf file, which worked for me:
[From the Ubuntuguide](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29)
[From the offical Compiz site](http://compiz.org/nvidia/)

---

### Post by Ndyanabo on 2007-09-24
yeah, it looks like I don't have: 
```
Section "DRI"
 Mode 0666
EndSection

```
in my xorg.conf at the moment, but I know I had it there at some point or other in my struggle over the weekend. I didn't come across that particular ubuntuguide howto, but I think I found one that had pretty much the same instructions, as I remember enabling these:
```
Load "dri"
Load "vbe"
Load "glx"

``` to no avail. 

I also looked at that compiz.org page too, but at the moment it's not loading for me.

Anyway, it looks like Forlong has identified a problem.

---

### Post by Forlong on 2007-09-24
I recommend reconfiguring your xorg.conf

You can do a backup first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then run this:
```
sudo dpkg-reconfigure xserver-xorg
```
Set everything as accurate as you can. Look for your monitor's manual first.

Afterwards, run this to configure it correctly:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by Ndyanabo on 2007-09-24
I'm not at home now, but I'll happily try that again do it when I get back. However, that's essentially the procedure that I used to create the current xorg.conf.

I'll also try the DRI thing suggested in the ubuntuguide.

However, let me say that 

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
``` returned some sort of error last time. When it didn't work, I put the following line in the "screen" section of the xorg.conf: 
```

    Option 	   "ARGBGLXVisuals" "True"
``` Does that nvidia-xconfig line do more than that?

if I get the error again, I'll post it.

I don't have the monitors manual. Like the computer itself,  I pulled it out of an office store room. Circa 2003 Dell, common stuff. Anything I need to look out for?

---

### Post by Ndyanabo on 2007-09-24
confusion!

I'm looking at the offical Compiz site that petit.padavoine suggested, and they say *not* to enable DRI. anyway, I think I tried that too at some point.

But they also say that 
```
glxinfo | grep "OpenGL version string:"
```
should return
```
OpenGL version string: 2.1.0 NVIDIA 96.31
```

I notice from my first post that I have:```
OpenGL version string: 1.5.3 NVIDIA 71.85
```

is that because I'm using the legacy driver?  Compiz says to use the Latest Nvidia driver. Should I try to remove the legacy driver and install the latest one? I've seen several lists that show my card isn't supported on the new drivers and that I should use the legacy driver.

---

### Post by Ndyanabo on 2007-09-24
so, following the compiz recommendations, I added:
```
Option         "DisableGLXRootClipping" "true"
```
to "screen" section of the xorg.conf. Restarted X, tried to run compiz, nothing.

moved on to Forlong's recommendation:
```
$ sudo dpkg-reconfigure xserver-xorg
```

then here's the error I mentioned:
```
$ sudo nvidia-xconfig --add-argb-glx-visuals -d 24
Password:
nvidia-xconfig: unrecognized option: "--add-argb-glx-visuals"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.

```

Weird. So, I manually added:
```
Option         "AddARGBGLXVisuals" "true"
Option         "DisableGLXRootClipping" "true"
```
to screen, and

```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

also noticed that the dri was enabled in modules, and that there is that dri section with the 0666 mode, contrary to the Compiz suggestion.

in any event, after making those changes, again, no compiz effects.

anything else to think about?

---

