---
title: "Get a black screen if beryl-manager is started"
date: 2006-11-21
forum: Desktop Environments
---

### Post by tomcheng76 on 2006-11-21
Hi, guys
i got a blank screen with a cursor only if beryl-manager is started on startup.
I am using a P4 (no HT) CPU. GF4 MX440 VGA and Ubuntu Edgy.
I am using the guide here [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)
Here is my xorg.conf, thanks in advance

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
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
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

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "KF-573"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Monitor        "KF-573"
    DefaultDepth   24
    Option	   "ExactModeTimingsDVI" "TRUE"
    Option	   "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Rajiv_Nair on 2006-11-21
im on an ATI.....but still beryl used to crash on startup for me too..after a lot of "crash" tests.i found dat everythin went fine if my cable modem wasnt pluggd in at startup..this mite b wrong....but wrkd for me:D

---

### Post by tomcheng76 on 2006-11-22
Now i follow this wiki
[Install /Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")
First i have to create a new XGL login session
then i create a startxgl.sh as following
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session

Now i am able to run beryl if i type beryl-manager
However, i want it to run automatically when i choose XGL this login session
Then i try to use this new startxgl.sh as following
#!/bin/sh
beryl-manager
sleep 4
exec gnome-session

Then i get cursor and a blue (my background color) screen again......
However, it is not a black screen anymore , improved ? :-D  ](*,)

---

### Post by tomcheng76 on 2006-11-22
Now, by putting /usr/bin/beryl-manager into auto startup of session setting. It solves the startup problem.
However, why does my icon and gnome-bars are so ugly?
Here is the picture
[IMG]http://img207.imageshack.us/img207/148/xglap9.png[/IMG]

---

### Post by Rajiv_Nair on 2006-11-22
small piece of advice..running beryl-manager in starup aint the best of ideas.trust me.ur way better off creattin a launcher on ur desktop and runnin it after XGL comes up without any probs

---

### Post by Rajiv_Nair on 2006-11-22
dude..if ya hv beryl and xgl installed then goto [http://forum.beryl-project.org/topic-4704-vista-compiz-aualin](http://forum.beryl-project.org/topic-4704-vista-compiz-aualin) and do watever is tld.be the proud owner of an uber sexy desktop:D

---

### Post by tomcheng76 on 2006-11-22
after crashing again and again , including installing beta nvidia driver, uninstall all nvidia thing and reinstall xorg driver , dpkg reconfigure xorg-server , reinstall nvidia...reinstall .....

Finally, i got my GNOME session running beryl without any problem :D 
Now i have a stupid question.
Can i use color depth 16 instead of 24, as some windows applications need 16bpp
if i set 16 in xorg.conf, anything just becomes messy and i cant see anything [-( 

However, all google things i found is talking about 16 => 24
Anyone has idea? :roll:
Thanks in advance

Thanks Rajiv_Nair, i will go there to have a look

---

