---
title: "Compus Fusion doesn't work (Gutsy), but Beryl used to work (Edgy)"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by mike_richman on 2007-11-17
I know there are many, many posts about Compiz trouble, but I've waded through a number of them and I can't find any that match my particular problem...

Under Edgy, I installed Beryl from some repositories as recommended somewhere on this forum.  It worked beautifully.  I completed the upgrade to Feisty painlessly.  But when Ubuntu started supporting Compiz Fusion by default in Gutsy, I removed every package related to beryl, emerald, and compiz, and then I completed the upgrade.  Now compiz won't work for me at all -- says "desktop effects cannot be enabled".

When I run "SKIP_CHECKS=yes compiz", compiz does load, but I can only view the top-left quarter of the screen.  Of that, only the GNOME panel and title bars are visible.  Windows are black.  Alt-tab works, but the window previews are also black.  My gut tells me there is a memory issue, but it doesn't make sense that the allegedly sloppy/unstable Beryl worked on my card while Compiz seems to need more RAM.

There are so many people dealing with this sort of issue, so I don't expect an instant fix, but any help or advice is greatly appreciated.

Here's my card:
```

$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)

```

I have the following packages matching the string "nvidia" installed:
```

nvidia-glx nvidia-kernel-common

```

Here is the output from running compiz on the command line:
```

$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

Here is the output from running SKIP_CHECKS=yes compiz on the command line:
```

$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaSKIP_CHECKS is yes, so continuing despite problems.
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Here is my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
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
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection


Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Driver         "nvidia"
    Option         "TripleBuffer" "True"
    Option         "NoLogo" "True"
    Option         "XAANoOffscreenPixmaps"

#    Option         "TwinView" "True"
#    Option         "TwinViewOrientation" "RightOf"   
#    Option         "UseEdidFreqs" "True"
#    Option         "MetaModes" "1490x900,1024x768; 1024x768,1024x768"
#    Option         "UseDisplayDevice" "CRT" 
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by Zorael on 2007-11-17
> Here is the output from running SKIP_CHECKS=yes compiz on the command line:
```

$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaSKIP_CHECKS is yes, so continuing despite problems.
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Besides needing the SKIP_CHECKS part, that actually looks right. It seems to always complain about that YV12 image format thing.

In what way doesn't it work? No window decorations (titlebars, etc)? I don't completely follow.


While I've no idea what could cause your specific problem, *know* that many issues arise from having remnants of old Compiz/Beryl installations still in your system. You need to pick Complete Removal in Synaptic, Request Purge in Adept Manager, or do 'apt-get purge' in the terminal to get rid of said remnants.

```
sudo apt-get purge compiz* libcompiz* beryl* libberyl* emerald* libdeco*
```

Then reinstall and see if it works.


Also, the AllowGLXWithComposite option in xorg.conf seems mandatory, from what I hear.
```
    Option         "AllowGLXWithComposite" "True"
```
As for whether it should be in the Screen section or the Device section; I've heard conflicting evidence, so I put all options in both.

---

### Post by mike_richman on 2007-11-17
I purged those packages as you recommended.  A note for anyone reading this, though: apt-get purge does a regex match, so 'compiz*' matches any package with compi + 0 or more z's.  For example, all packages with 'compile' in the name... So use this instead:
```

sudo apt-get purge compiz.* libcompiz.* beryl.* libberyl,* emerald.* libdeco.*

```

I also added the AllowGLXWithComposite option in my xorg.conf, but the behavior is the same.  I've attached two screenshots -- one with Compiz running, the other with Metacity running.

Another note: compiz complains that I have less than 64 MB of video RAM, but according to lspci, it is a 64 MB card.  I wonder if compiz is unable to detect, and thus unable to use, all of the RAM?

-Mike

---

### Post by Zorael on 2007-11-17
Hmm, okay. I've never seen this issue so I can but help troubleshoot.

Does this work?

```
$ compiz --replace --indirect-rendering &
```

---

### Post by mike_richman on 2007-11-17
Thanks a lot for following up.  --indirect-rendering actually did help.  I only had access to the top-left quarter of the screen again, but windows were mostly filled in / not black.  There were drop shadows and title bars were partially transparent.  Funny thing is, once I got my terminal into the top-left quarter, it stuck to the edges of that region the way it normally sticks to desktop edges or other windows!  So now I'm thoroughly confused, but possibly one step closer to the solution...

Here is the new output:
```

$ SKIP_CHECKS=yes compiz --replace --indirect-rendering 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaSKIP_CHECKS is yes, so continuing despite problems.
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

-Mike

---

### Post by Zorael on 2007-11-17
Could this be the infamous Nvidia Black Window bug? I've never seen screenshots of it, but there's certainly blackness on your desktop where it shouldn't be any.

Googling quickly I found [http://forum.compiz-fusion.org/showthread.php?t=1762](http://forum.compiz-fusion.org/showthread.php?t=1762). There's likely more out there.

---

