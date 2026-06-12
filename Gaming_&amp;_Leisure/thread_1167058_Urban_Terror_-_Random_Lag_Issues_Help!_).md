---
title: "Urban Terror - Random Lag Issues Help! :)"
date: 2009-05-22
forum: Gaming &amp; Leisure
---

### Post by GremlinZ on 2009-05-22
Hi, Im new to using linux and would like to get my favorite game to work (Urban Terror). I know my system is old but its all i have atm.

My issue is this.
 
 When i run Urban terror and boot into a private server to test my fps (a server ran on my own pc with no one else on it), Most of the time i get  45 fps and the game lags. Though sometimes i get smooth game play with 85 frames per second steadily after playing with and saving  the XServer settings.
Once i get the 85 fps the game becomes playable, so i close the game down and restart it so i can find public server to play on, but once i join one my fps goes bad again. I know this isnt because of the extra load with interacting with other players, as once before it stayed ok at 85 in a public server, untill i reoaded a game setting which made it bad , and i havnt been able to get it to work again.
 
I have all settings at the lowest, and have configured the Nvidia X server as best i can understand.

Everything is loading fine, the game textures etc and it runs ok, no freezes, and it can run the 40 fps really steadily, but as soon as i move around it lags hard. Especially when i move my mouse it lags more.

**This is what i have attempted so far to sort this issue.**

*Installed the latest nvidia x server driver through :  system > administration > Hardware drivers
*Ive checked with EnvyNG that i have the latest driver. - i do
*Downloaded compiz fusion to turn compiz off. - worked fine once did nothing for game after
*Downloaded ubuntu tweak - did nothing
*Installed WINE and run the game fine. - worked once then no joy
*Set the X Server up as best i know and saved the settings to the xorg.conf file
*Configured my xorg.conf adding in a few lines i read would help
*Posted in the Urban Terror Forums
*Ran GLX Gears though i dont know what to do with the info.

I have also set the in game options to match the resolution, color depth and turned all settings down or off ingame.
Added "Coolbits" to the xorg.conf file = Which worked a few times showing me the overclock frequency option, and now isnt there even though "Coolbits" is in the xorg.conf file.
I have tried reading multiple forums both ubuntu based and game related but hav'nt found the answers that solve my problems.

**My sytem specs :**

623 mib
AMD Atlon 1Ghz processor
Nvidia Geforce 6200 
200 gb hard drive
Razor DeathAdder
**Operating system =**

Ubuntu 9.04
Kernal Linux 2.6.28-11-generic
Gnome 2.26.1

**Nvidia Driver Version 180.44 (Updated by Envy)**

**X Server display Configuration :**

Display tab : 
Model                   = NEC FE700 (CRT 1 on GPU 0 )
Configuration       = Seperate X Screen
Resolution            = 1024 x 768
Monitor Refres h  = 85 Hz

X Screen tab: 
Screen Number = 0
Color Depth       = 24

**X Server XVideo Settings : **

Video Texture Adapter = Sync to VBlank is Off
Video Blitter adapter     = Sync to VBlank is Off

**Cursor Shadow : **

Enable Cursor Shadow = Off

**OpenGL Settings: **

Sync to VBlank =  Off
Allow Flipping    = On
Image Settings = High Performance 

**Anti Aliasing Settings :**

Antialiasing               = Off
Anistropic Filtering   = Application overide x1
Texture Sharpening = Off

**My xorg.conf : **

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"Nvidia Driver Version 180.44 (Updated by Envy)

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC FE700"
    HorizSync       31.0 - 70.0
    VertRefresh     55.0 - 120.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    Option         "Coolbits" "1"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768_85 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

**GLXgears info : **

5862 frames in 5.0 seconds = 1172.361 FPS
6588 frames in 5.0 seconds = 1317.505 FPS
5601 frames in 5.0 seconds = 1120.150 FPS
8608 frames in 5.0 seconds = 1721.589 FPS
11206 frames in 5.0 seconds = 2241.083 FPS
10576 frames in 5.0 seconds = 2108.645 FPS
11906 frames in 5.0 seconds = 2381.090 FPS
11304 frames in 5.0 seconds = 2260.703 FPS
12706 frames in 5.0 seconds = 2541.188 FPS
12612 frames in 5.0 seconds = 2522.219 FPS
9239 frames in 5.0 seconds = 1847.297 FPS
8929 frames in 5.0 seconds = 1785.793 FPS
10373 frames in 5.0 seconds = 2074.578 FPS
11067 frames in 5.0 seconds = 2212.778 FPS
9855 frames in 5.0 seconds = 1970.879 FPS
8851 frames in 5.0 seconds = 1770.129 FPS
10491 frames in 5.0 seconds = 2098.083 FPS
10034 frames in 5.0 seconds = 2006.789 FPS
11507 frames in 5.0 seconds = 2301.364 FPS
12663 frames in 5.0 seconds = 2532.453 FPS
12375 frames in 5.0 seconds = 2474.953 FPS


                                                                          .................................................

---

### Post by GremlinZ on 2009-05-25
bump - edited my post and added some more relevant info.

Does anyone have any ideas as to whta i can try next?

---

### Post by afderrick on 2009-08-05
No I have the same problems.  They are VERY specific to 9.04 as when I rolled back to 8.10 the problems fixed themselves.  Try using a more stable version of Ubuntu.  9.04 has been a disaster, I'm personally considering switching distros if Canonical keeps messing things up.

---

