---
title: "Ubuntu , nvidia and dual wiew problem"
date: 2006-06-27
forum: Desktop Environments
---

### Post by ExtruderNOR on 2006-06-27
I am an linux n00b .    ](*,)    ;) 

I have bought a laptop based on MSI 1032 barebone - [http://www.msicomputer.com/NB/product_spec.asp?model=MS-1032](http://www.msicomputer.com/NB/product_spec.asp?model=MS-1032)  . 

I have installed Ubuntu 6.06 . I have followed a how-to and installed the latest Nvidia driver . 

I am connecting a old Hansol CRT to the laptop .  After a lot of work I got twin wiew to work , but the CRT is automaticly choosed as the primary screen . Is there anyway I can deside what screen is the primary ? 

The CRT screen is 4:3 and the laptop screen is widescreen .
In screensolution under "System" is says 2560x1024 at 50 Hz - so watching the CRT for long periodes of time makes my head hurt .  :rolleyes: 
Is there any way I can set up diffrent screensolutions for eacth monitor ? the nvidia controll panel detect the two monitors but I can`t set resolutions og refresh rates there ? 


My xorg.config file    - a little messy but ...


Section "ServerLayout"
    Identifier     "TwinView Configuration"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
Option "Xinerama" "Off"
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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
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
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce Go 6600]"
    Driver         "nvidia"
    Option	   "TwinView" 		"true"
    Option         "TwinViewOrioentation"     "Rightof"
    Option         "metamodes"   "1280/800,1280/800 ; 1024/768,1024/768 ; 1280/800,NULL ; 1024/768,NULL"
Option "Coolbits" "1"
Option "SecondMonitorHorizSync" "UseEdidFreqs"
Option "SecondMonitorVertRefresh" "UseEdidFreqs" 
    Option         "Monitor Layout"    "DFP, CRT"
    Option         "Clone"        "false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce Go 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Viewport 0 0
        Depth       1
        Modes      "1280x1024" "1280x800" "1024/768"
    EndSubSection
       SubSection     "Display"
        Viewport 0 0
        Depth       24
        Modes      "1280x1024" "1280x800" "1024/768"
    EndSubSection
EndSection

](*,)   I am grateful for any advice

---

### Post by ExtruderNOR on 2006-06-27
Can anyone help me ?

---

### Post by ExtruderNOR on 2006-06-29
[QUOTE=ExtruderNOR]Can anyone help me ?[/QUOTE]

Bump - cant anyone help ?  I really could use tips here ?

---

### Post by derrickh on 2006-07-11
I recently installed the new ATI driver fglrx 8.26.18 and am running into the same problem.  I can't find where in the xorg.conf file the primary monitor is set.  By default, my DVI output of my vid card is always set as the primary monitor.  I have a x800GTO.  If I find anything in the forums or IRC, I'll post it here.

---

### Post by arnieboy on 2006-07-11
The reason why your CRT monitor is being used as default is because  Monitor is set as "Generic Monitor" under Section Screen (the last section) 
The "Generic Monitor" identifier is set below Section "Monitor" which is your CRT monitor. 
You probably need to add another **section** which refers to your laptop monitor and give it a suitable identifier name like "Laptop Monitor"  instead of "Generic Monitor" and call that from Section "Screen" .

whatever u do, first BACKUP your existing xorg.conf

---

### Post by dboot on 2006-07-11
> **arnieboy said:**
> You probably need to add another **section** which refers to your laptop monitor and give it a suitable identifier name like "Laptop Monitor"  instead of "Generic Monitor" and call that from Section "Screen" .

What will be the difference between the sections?

Do you mean:
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "LCD Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Monitor        "LCD Monitor"
```

I have twinview set up with an LCD and a CRT monitor. I want to switch my main desktop from my CRT monitor to my LCD monitor.

---

### Post by arnieboy on 2006-07-11
no just ignore my last post about creating two monitor sections and do the following:
add the following line in Section "Device"
> Option "ConnectedMonitor" "DFP,CRT"
save and exit and restart your computer. 
one caveat though:
If your LCD monitor is connected externally (not a laptop screen), and does not use DVI cables (uses analog ones instead) the above line must look like the following:
> Option "ConnectedMonitor" "CRT,CRT"

---

### Post by dboot on 2006-07-11
After adding this line, my CRT monitor is still my default monitor. 

Maybe there's another solution...

Is there anyway to change my right and left desktops? Physically I have my LCD on my left and my CRT on my right. However, my CRT has the left side of my desktop and my LCD has the right side. Again, is there a way to flip my desktop without physically moving my screens? Thanks!

---

### Post by zc923 on 2006-07-12
The Two resolution issue can be fixed by using Option "MetaModes"
Add this under your Device Section of your xorg.conf
First, you need to know the optimal resolution setting of your monitors. For the this purpose, we will say that that your Primary (CRT, as you said) has a resolution of 1280x1024, and your secondary, your LCD screen has 1024x768.

As you currently have your metamodes, it doesn't seem like it will work.

```
Option "MetaModes" "1280x1024,1024x768"
```

For your orientaion, you want your Secondary to display to the right of your primary

```
Option "TwinViewOrientation" "RightOf"
```

The above codes are in my Xorg file, and they work for my dual setup.

I'm not skilled in the refresh rate issue. Although I'm pretty sure your UseEdidFreqs won't work for the CRT. My best guess is you are going to need a input a range of possible values. WARNING: Don't do this unless you are positivly sure that the range you have selected is within the the monitors capabilities. Any other could damage your monitor. Your best bet would be looking up some documentation at Xorg as well as the monitor manufacturer

---

