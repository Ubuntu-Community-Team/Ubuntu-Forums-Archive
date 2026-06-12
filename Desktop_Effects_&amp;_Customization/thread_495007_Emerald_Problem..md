---
title: "Emerald Problem."
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by shafin on 2007-07-07
I've first installed compiz fusion,its running fine.Then I installed Emerald from synaptic,so beryl core was also installed with it,but beryl manager was not installed.Now the problem is,whenever I try the emerald --replace command,my window borders and top bar vanishes.The bar is still there,as I can drag the invisible one,even the invisible minimize,close etc.

I've seen in other threads the same problem with beryl,but not one with compiz fusion.

I'm on feisty 64 bit,with a intel GMA 950.

Thanks

---

### Post by RebounD11 on 2007-07-07
Try compiz --replace -c emerald

---

### Post by shafin on 2007-07-08
> **RebounD11 said:**
> Try compiz --replace -c emerald
No success,with this command,compiz loads,but emerald does not.When I load only emerald,I get this:

---

### Post by hyperair on 2007-07-08
If you use nvidia, try this command and restart your X server:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```

---

### Post by shafin on 2007-07-08
> **hyperair said:**
> If you use nvidia, try this command and restart your X server:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```
I'm on intel GMA 950 :(

---

### Post by shafin on 2007-07-09
NO help??:(

---

### Post by hyperair on 2007-07-09
Go to CompizConfig Settings Manager and make sure your window decoration plugin is enabled.

---

### Post by shafin on 2007-07-10
> **hyperair said:**
> Go to CompizConfig Settings Manager and make sure your window decoration plugin is enabled.
That's enabled.

I also tried the xconf editing,and that failed also

---

### Post by shafin on 2007-07-10
> **shafin said:**
> That's enabled.

I also tried the xconf editing,and that failed also
BTW,when I tried Emerald from Terminal,it gave me the following output

```
-desktop:~$ emerald --replace

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7334): Wnck-WARNING **: Unhandled action type (nil)



```

---

### Post by hyperair on 2007-07-10
Strange. Could you try make your terminal transparent and post here whether it works or not? You can change the opacity by going to Edit->Current Profile->Effects.

Also, make sure your xorg.conf has this at the bottom
```

Section "Extensions"
Option "DAMAGE" "Enable"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection

```

---

### Post by rickycodie on 2007-07-10
i had this same problem i found that the version that emerald is and the version that compiz looks for are different, but i have no idea how to fix it. i got rid of fusion in favor of beryl.

---

### Post by hyperair on 2007-07-10
Well, if you installed the packages from Trevino's repository, the version mismatch shouldn't arise.

---

### Post by shafin on 2007-07-10
> **rickycodie said:**
> i had this same problem i found that the version that emerald is and the version that compiz looks for are different, but i have no idea how to fix it. i got rid of fusion in favor of beryl.
How do I find that?

---

### Post by shafin on 2007-07-10
[QUOTE=hyperair]Strange. Could you try make your terminal transparent and post here whether it works or not? You can change the opacity by going to Edit->Current Profile->Effects.

Also, make sure your xorg.conf has this at the bottom
 	Code:
 	Section "Extensions"
Option "DAMAGE" "Enable"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection 
[/QUOTE]I can get the Terminal transparent,screenshot is attached.


I updated the xorg.conf file,still the problem persists.Finally,I tried heliodor,and this one gives me vanished borders also,with these returns

```
-desktop:~$ heliodor --replace

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)

(heliodor:6039): Wnck-WARNING **: Unhandled action type (nil)


```





And here is the complete xorg.conf file

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us,bd"
    Option        "XkbVariant"    ","
    Option        "XkbOptions"    "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
Option "DAMAGE" "Enable"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection
```

---

### Post by shafin on 2007-07-13
2 days..no help.
Am I left on the Desert?

---

### Post by Mongoose.wa on 2007-07-13
I installed the same stuff as you yesterday (Compiz Fusion, then Emerald through Synaptic), but they both seem to work fine. My only issue is that my top and bottom panels aren't themed.

Before I finally got CF working though, every time I'd try to install it, my window decorations would disappear. In my case, I fixed it by deleting software sources that were doing something to mess stuff up. I doubt this would apply in your case, but you never know.

---

### Post by enrigp on 2007-07-15
I had the same problem, the borders not work emerald not work.
I have a Nvidia Geforce Go 7600 and try the solution: "nvidia-xconfig --add-argb-glx-visuals" and now work!!!!
thanks!!!, but what do this command?

---

### Post by hyperair on 2007-07-15
If you're asking what this command does, it's an automated way provided by nVidia to configure your xorg.conf file to enable ARGB GLX Visuals in your X server. ARGB = Alpha Red Green Blue. I think this means it allows translucency to be set in certain parts of the window, instead of the entire window. Alpha denotes Opacity, just so you know. GLX.. I'm not sure what it means, but GL means Graphics Layer. It's to do with 3d stuff, so it's required for Compiz Fusion/Beryl

---

### Post by shafin on 2007-07-28
Problem solved.:D

This problem was caused by incompatible versions of Compiz Fusion and Emerald.Emerald was version 0.2.1,which was for Beryl only.So I installed version 0.3.0 which is for both emerald and beryl.

However,I had to completely remove and reinstall compiz to get this to work.And one more small problem.Now I cant get the metacity themes to work with compiz.They worked fine previously.

Thanks to everyone who helped.Thanks a lot.

---

### Post by hyperair on 2007-07-28
Thing is, you either use Emerald themes or Metacity themes at one point of time. If you want Metacity themes, you can try this:
```
gtk-window-decorator --replace
``` or ```
heliodor --replace
```

whichever works for you.

---

