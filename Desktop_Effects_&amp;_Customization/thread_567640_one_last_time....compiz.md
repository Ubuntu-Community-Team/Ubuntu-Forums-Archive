---
title: "one last time....compiz"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by DOH on 2007-10-04
I need some help...I have been trying to find an answer to my problem for 3 weeks](*,) <--me.
I used forlong's installation guide to help me.  

but when I try to run compiz it takes away my window titlebar and I cant drag windows around.

Any help at all to get this fixed would be appreciated..thanks everyone.

---

### Post by Locutus_of_Borg on 2007-10-04
do you have window decorations enabled?

---

### Post by DOH on 2007-10-04
yeah
in compiz-settings-manager's window decorator command line i have gtk-window-decorator.
that is what the guide told me to do.
i have also tried running emerald in the command line and that doesn't work either.

---

### Post by Locutus_of_Borg on 2007-10-04
do you also have beryl?

after i installed compiz fusion, things were running kind of buggy until i opened beryl settings manager and unchecked everything

i dont really know as i am rather new to this myself

---

### Post by Faud on 2007-10-04
> **DOH said:**
> yeah

i have also tried running emerald in the command line and that doesn't work either.

It would be emerald --replace

and can you alt+left click to move the windows around ?

---

### Post by DOH on 2007-10-04
I can't move windows at all.

I got rid of compiz and emerald all together.  I downloaded beryl and the same thing happens when i run that too. any ideas.

---

### Post by ssteinbr on 2007-10-04
I had the same problem and adding
```
Option "AddARGBGLXVisuals" "True"
```
to the Screen section of my xorg.conf did the trick.

---

### Post by DOH on 2007-10-04
how do i do that exactly..
Please forgive the ignorance. This OS has a sharp learning curve.

---

### Post by Rupertronco on 2007-10-05
Well first tell us what type of video card you're using and what driver. Second if you're unfamiliar with editing config files with a text editor I'm not sure compiz is the best idea, but we'll try. We need you to post your xorg.conf file. To do that type ```
 gedit /etc/X11/xorg.conf 
```. 


Copy that file and paste it here. Also, go to a terminal and type ```
 glxinfo
``` and paste the output of that.

Now when you go to edit that file, you'll need to give gedit super user privleges by adding "sudo" to the begging of that command.

---

### Post by Forlong on 2007-10-05
Compiz is not running at all on your machine.

Post the output of
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by DOH on 2007-10-16
output of  grep -v ^# /etc/X11/xorg.conf

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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation C51 [Geforce 6150 Go]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51 [Geforce 6150 Go]"
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

---

### Post by Forlong on 2007-10-17
What's the output of ```
compiz
```
Use the forum's CODE tag please (# button)

---

### Post by DOH on 2007-10-17
I got it working last night at 3 am.  So happy I went to sleep immediatly.
thanks forlong your help was irreplaceable.
I used a command that you posted in another thread that fixed everything for me.
 

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

thanks again

---

