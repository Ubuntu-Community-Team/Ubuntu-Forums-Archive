---
title: "ATI roblem : Dual Monitors"
date: 2009-10-07
forum: Desktop Environments
---

### Post by ShapeShiftme on 2009-10-07
Good Day All.

I have been using linux for years but never ubuntu. 
I normally used Suse (For basic Desktop) And Gentoo (For Servers)

I just got a HP DV7 2104tx  Laptop
Its A beauty. I however as my preferred choice tried to run SUSE. Now that was a flop of note. With the laptop having a ATI Radeon Mobility HD 4650 on it. Suse did not have a driver. I then thought ill try out a new distro. 

I remember trying ubuntu YEARS ago when it basically started and wasnt to fond of it. Cant really remember why. But i also prefer KDE. (Personal Choice). Then i found out that ubunto had the latest propitery drivers it was awsome and i was so happy. I installed kubuntu. 

And what do you know I have 3d effects in less than 10 min after finish install. And im damm happy with how ubuntu runs. I can do everything from Nokia bluetooth conection, audio... etc.

So kubunto has even got me to use linux over windows. Never thought that would happen. 

But i only seem to be having one problem.
Dual Monitors:

I have tried everyhting. From  using "aticonfig" to the "ati catalist GUI" even tried some randr settings gui and console.

What i have been able to break so far "I can either get 2 montirs to clone" (Clone is astupid option) Then on next reboot Scrren flases alll the time as is kde is restating or x.

The next option that seemed to have got further was me using ati calaist controll gui.I was able to turn it on then reboot. the screen did not flash but then the scrren resolution was so big i could only see the top left conor of the login form at the lower right of my mon. As if someone set my res to 800x600 but didnt resize it.

So basically if someone can help me i would be extremely greatfull as im a desighner. web and developber. so at least 2 mon is a must.

Here is my currently working default xorg.conf (Only one monitor Works)

```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "True"
EndSection

```This is after i used the ati controll center but then i broke it while manually trying to fix it.

```

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "Default Screen" 0 0
    Screen         "amdcccle-Screen[1]-1" 1600 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "on"
    Option        "DontZap" "True"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[1]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    Option        "Mode2" "1600x900,1024x768,800x600"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Mode2" "1600x900,1024x768,800x600"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Mode2" "1600x900,1024x768,800x600"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    Monitor    "amdcccle-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1600x900" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    Monitor    "amdcccle-Monitor[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1600x900" "1024x768" "800x600"
    EndSubSection
EndSection

```If somebody could put me on the right track i would be greatfull.
Perhaps if someone even has a xorg.conf to display me as an example.

Regards
Donovan

---

### Post by ShapeShiftme on 2009-10-07
UPDATE : Ok i got the displays to work. Alot of effort and struggle.
But they are working. I must not goto display settings as that will overwrite the ATI config settings and ill have to reboot.

There are 2 little things if some one could please help.

Big Desktop: Ive got the system working with big desktop. Which is nice and technically does what i want. However the display reselovtion of the second monitor is 2 low. As big desktop basically creates a virtual desktop" and shares it in beteen the monitors. i see ATI has a "Independant display option"

Over there i can set the individual monitor sizes. But 2 things happen. One my taskbar doesnt show anymore. And and i cant drag windows to the other display.

Does any one know there way around theese problems


No 2: 
This is a laptop i take to clients. How does one stop the second display and sart it easily again when i get back to the office.'

Regards
Donovan

---

### Post by ShapeShiftme on 2009-10-09
OK I got it working. damm its hard. but awsome none the less. I got it to have sepetate mnitors with different resolutions Not as big desktop so all windows workon on the monitors independantly. I plan to give the steps later for whoever might need it. At the same time ill post the setps for sound etc.

Chat later all

---

### Post by Dom1noe on 2009-10-12
From your description I think I have the same problem you did. But as I am sort of a linux newbie I hope I could use your solution as well ;)
I have two monitors plugged in and they're displaying the same actually.
I'm currently on this graphics card: VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e) as my one is in repair. I don't even know which drivers are best for me so this is something where I could use a hint as well... ;)
Post any piece of advice. I'll be glad for it.

---

