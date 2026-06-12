---
title: "Ubuntu 9.10 + Intel + Compiz + Emerald.....is it possible ?"
date: 2009-11-27
forum: Desktop Environments
---

### Post by _mikec_ on 2009-11-27
I have installed Ubuntu 9.10 and i am trying to activate desktop effects to use compiz and emerald. From /System/Administration/Hardware Drivers the list is empty. I had to figure out why in Karmic there's no xorg.conf file, this is because now, everything is auto detected by X server. What do i do if i need to modify xorg.conf but it isn't there ???? i had to kill all X (ctrl+alt+backspace) and in terminal run sudo xorg -configure, this created a Xorg.conf.new in my Home Directory which then i transfered to /etc/X11/xorg.conf. Nothing happens when i try 
" sudo dpkg-reconfigure -phigh xserver-xorg "[B]

My questions is[/B]:
How do i activate desktop effects ?? if the system doesn't want to tell me the recommended driver for my video card ?

[http://forum.compiz.org/showthread.php?t=10238](http://forum.compiz.org/showthread.php?t=10238)

**This is for Jaunty not for Karmic!**
[http://ubuntuforums.org/showthread.php?t=1130582&highlight=Intel+Corporation+Chipset](http://ubuntuforums.org/showthread.php?t=1130582&highlight=Intel+Corporation+Chipset)

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I have attached my Xorg.log for reference.

---

### Post by howefield on 2009-11-27
Have you tried setting Visual Effects in System > Preferences > Appearance to Normal or Extra ?

Install compizconfig-settings-manager with Synaptic Pacakage Manager to set extra features.

---

### Post by _mikec_ on 2009-11-27
I have, but i get an error saying " Desktop effects could not be enabled "

# mike@mike:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity

> To bypass the compiz-manager blacklist on various video cards and drivers, run:# mkdir -p ~/.config/compiz; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager 

this actually does not work for me, it does bypass the check but, when i run the command and then type compiz --replace, all windows disappear or my computer hangs.

---

### Post by _mikec_ on 2009-11-27
my xorg.conf
> Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
    Load  "glx"
    Load  "dri2"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Option      "AccelMethod"            "uxa"
    Option      "EXAOptimizeMigration"        "true"
    Option      "MigrationHeuristic"        "greedy"
    Option      "Tiling"            "true" # i8xx users: see note in guide
        VideoRam 130560
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


---

### Post by _mikec_ on 2009-11-28
does compiz even support Intel 82845G chipset ??? how do i tell if it does or not ?

---

### Post by Rody on 2009-11-28
I am no expert but it kinda looks like you need to load up some hardware drivers for your video. I know that Intel has the absolute worst 3d drivers but if you dig around you should be able to find some to make compiz work.

rody

---

### Post by growlf on 2010-01-06
I am having identical issues on my daughter's Dell.  Same card, same errors, same version (Karmic).  Until I created an xorg.conf file, every so often when she did updates she would get a black screen for 2 or three reboots and a log entry stating that i810 driver could not be found.   Anyone have any solutions yet?

---

### Post by rossofiorentino on 2010-01-15
I have a Nec PowerMate Vl4 with same integrated graphics card, and I must say that also it doesn't work for me.
But i must say that i have tried live Knppix 6.01 and compiz works very very very well!!!!
What is the problem?
I don't know if can be useful, bau i wont to tell:
lsmod say that i915 module is loaded, but is it right?
If my chipset is G82845, why i915?

I love compiz, i wuold like to use it.....

---

