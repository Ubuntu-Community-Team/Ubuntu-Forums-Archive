---
title: "Compiz Config can open but nothing works!"
date: 2007-09-10
forum: Desktop Effects &amp; Customization
---

### Post by chrisruls00 on 2007-09-10
I have installed It and can open its config menu, But when I activate the plug-ins nothing works!

---

### Post by hyperair on 2007-09-10
Did you start Compiz Fusion?
```
compiz --replace -c emerald
```

or if you don't have emerald
```
compiz --replace
```

---

### Post by chrisruls00 on 2007-09-10
Im pretty sure I did that. I think this might be related to my NVIDIA driver problem. Ill fix that problem first.

---

### Post by hyperair on 2007-09-10
You could try it in the terminal, and see what the output is like.

---

### Post by chrisruls00 on 2007-09-10
It says:

chrisruls00@chrisruls00-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted 'nv' driver is in use 
aborting and using fallback: /usr/bin/metacity 


Hmm, I'm new to Linux but I'm sure this means I missed installing something.

---

### Post by Forlong on 2007-09-10
> **chrisruls00 said:**
> Hmm, I'm new to Linux but I'm sure this means I missed installing something.
Yup, you need to install a nvidia-glx driver.
If you're on Ubuntu (7.04 Feisty, GNOME) you can install it via *System &#8594; Administration &#8594; Restricted Drivers Manager*
Afterwards, run this command in a terminal to make sure your xorg.conf is configured correctly:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by chrisruls00 on 2007-09-11
Installing that driver caused colored lines to appear when I reboot Ubuntu, although I can use Ctrl+Alt+F1 to switch to the terminal after the lines appear.

---

### Post by chrisruls00 on 2007-09-12
ok I got the driver working (I think) but I still cant get it working. That old message still appears.

EDIT:Nope the driver dosen't work...

---

### Post by chrisruls00 on 2007-09-12
well i got a diffrent driver working BUT it says GLX not supported...

---

### Post by Forlong on 2007-09-12
Please post the output of this command
```
grep -v ^# /etc/X11/xorg.conf
``` in a terminal (and use the forum's CODE tag)

---

### Post by chrisruls00 on 2007-09-12
```
chrisruls00@chrisruls00-laptop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 420 Go]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 420 Go]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

also the driver I'm using is [http://www.nvidia.com/object/linux_display_ia32_1.0-7185.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7185.html)

In my NVIDIA X server settings i have the error:
The OpenGL extension 'GLX' is not supported by
the X server or there was a problem retrieving
GLX information from the X server.

when i run compiz I now get:
Checking for Xgl: not present. 
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by chrisruls00 on 2007-09-12
Ok i got it to where my nVidia settings app could recognize the Glx but compiz still cant detect the Xgl And keeps looking for texture_from_pixmap.

---

### Post by chrisruls00 on 2007-09-12
by the way I changed the xorg.conf file:

```
chrisruls00@chrisruls00-laptop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 420 Go]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 420 Go]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
    Option "Composite" "Disable"
EndSection
chrisruls00@chrisruls00-laptop:~$ 

```

---

### Post by hyperair on 2007-09-13
First of all, remove the block at the bottom where you disable Composite. Then restart your X server, and then go to a terminal and type: ```
glxinfo
```

---

### Post by chrisruls00 on 2007-09-13
Yay! Almost everything works now! My last problem is when I run Compiz The boarders to all my windows dissapear! I cant move them and my 3 buttons are gone...

---

### Post by hyperair on 2007-09-13
Firstly, you can move your windows by holding Alt and dragging them. Secondly, to fix the window decoration problem... Make sure you enable your Window Decoration plugin in CompizConfig Settings Manager, and then in that plugin's settings, set the "command" field to "emerald --replace". When you start up Compiz Fusion, use this command: 
```
compiz --replace -c emerald
```

---

### Post by Forlong on 2007-09-13
That depends on the packaged you used. The -c command works AFAIK only on Treviño's.
If you have used Amaranth's repo, you can see [here](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) in the "first steps", how to prevent window boarders from disappearing and later on, how to start compiz directly with emerald.

But I think your problem lies somewhere else - did you really run the command I recommended on the first site of the thread?
Because your default depth is set to 16 - but it needs to be 24.

---

### Post by chrisruls00 on 2007-09-13
I used the tutorial in Forlong's Sig to install compiz-fusion. It is set up to boot up when I log-in, so I type nothing in the terminal. I did not install Emerald, do I need to?

---

### Post by Forlong on 2007-09-13
> **chrisruls00 said:**
> I did not install Emerald, do I need to?
No, please type this in the terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Then restart your X-Server with pressing [Ctrl]+[Alt]+[Backspace]

If this still doesn't work for you, post your xorg.conf again.

---

### Post by chrisruls00 on 2007-09-13
Ok, Im at school now so I'll have to wait till I get home. Also to get my nVidia driver to work I had to add this line to xorg.conf under the Screen section:

option "UseDisplayDevice" "DFP"

---

### Post by chrisruls00 on 2007-09-13
Nope, im still missing the boarders of my windows

---

### Post by smartboyathome on 2007-09-13
type gtk-window-decorator --replace and post the output (this is included in fusion to replace windows with your default metacity theme)

---

### Post by chrisruls00 on 2007-09-14
Nope, nothing happens. BTW When I try to open a terminal with compiz open it just opens a white box. Also a few of the plug-ins dont work. The water effects dont work. Also I tried to download the advant-window-navigator because it looked cool but all it does is put a white box at the bootom of the screen. The 2 things that cause a white box are problbly related.

---

### Post by hyperair on 2007-09-14
White screen of death... on an nVidia. Not unheard of, but quite rare, especially with Compiz Fusion. Could you post your xorg.conf again please. Also, are you using XGL or not? If you are, that may be the source of the problem.

---

### Post by chrisruls00 on 2007-09-14
ok, as soon as I get home from school. I do know I have "Load glx" in my xorg.conf file, is that related to XGL?

---

### Post by chrisruls00 on 2007-09-14
Her e is my xorg.conf file. Also I just found out I cant open the default Text editor with Compiz either!

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

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
# Enable the composite extension

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
    Identifier     "nVidia Corporation NV17 [GeForce4 420 Go]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 420 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by chrisruls00 on 2007-09-16
anyone have a fix?

---

### Post by hyperair on 2007-09-16
Wait, I don't really understand what's going on. When you open a terminal, the terminal turns white, but not the rest of your screen, is that right? I take it that your terminal was supposed to be translucent to begin with. 
```

sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite

```

Try this out. It might work.

Btw, I was reading the previous posts and it seems you're using the 7185 driver. Why don't you remove that install nviida-glx instead? That contains the 9631 driver which I'm using as well, and should work for your card I reckon.

---

### Post by chrisruls00 on 2007-09-16
I have the 9639 driver installed now. It used to cause the GUI to not boot but I was told in another thread to add a line to xorg.conf and it then worked.

---

### Post by hyperair on 2007-09-16
What's the line you added?

---

### Post by chrisruls00 on 2007-09-16
screen 0
option "UseDisplayDevice" "DFP"

without those the driver will not work.

---

### Post by hyperair on 2007-09-17
I don't have that line in my screen section, but it works fine on my computer. What does that line do anyway?

---

### Post by chrisruls00 on 2007-09-17
IDK but before I added that line the driver always caused colored lines to appear instead of GNOME. By the way Im using a laptop. Someone who has the same graphics card as me told me I needed this line to make it use the LCD screen. And when I added the line it started to work.

---

