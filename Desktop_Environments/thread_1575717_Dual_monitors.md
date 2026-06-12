---
title: "Dual monitors"
date: 2010-09-16
forum: Desktop Environments
---

### Post by Cuco3 on 2010-09-16
I have a laptop running Ubuntu 10.04 that I use with a second monitor to have a multi monitor display.

My original setup was main monitor on the left and laptop monitor on the right.

I re-arranged my desk so that my laptop is on my left and main monitor is on the right

The problem I have is that when I drag the main display in the ATI control panel from the left to the right, it doesn't apply the settings. I noticed that when I restart and I go to log in, the displays are configured the way I want. When I log in, the settings revert back to the old settings.

Also, can someone tell me how to change the label of the monitors in the control panel (ie I want my main monitor to be 2 and my laptop monitor to be 1)

Can anyone help me out?

---

### Post by SlugSlug on 2010-09-16
Not sure if things have chaned in 10.04.. but can you post output of
```
cat /etc/X11/xorg.conf
```

---

### Post by Cuco3 on 2010-09-16
Thanks and here
> Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "PreferredMode" "1366x768"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "true"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
    SubSection "Display"
        Virtual   3046 1061
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3046 1061
        Depth     24
    EndSubSection
EndSection



---

### Post by Cuco3 on 2010-09-16
I'm wondering if the Ubuntu "monitors" is conflicting with the ATI. In my other computer with an nVidia video card, the "monitors" control panel would not allow me to configure the display when I had the nVidia proprietary drivers. This one lets me configure it.

BTW does anyone know how to reset my xorg to the ATI defaults?

---

### Post by Cuco3 on 2010-09-16
Man, Ubuntu 10.04 has been a real pain.

network manager doesn't want to auto log me in to my wifi network

ati's driver support sucks and I get screwed up open GL graphics

"Monitors" doesn't recognize that the ATI drivers are installed (which I'm sure is causing conflict)

and now I can't configure my dual monitors. I tried reverting to my old settings and even that doesn't work.

:o:o:o

---

### Post by SlugSlug on 2010-09-16
am not to sure with ATI so backup xorg.conf and
```
aticonfig --initial
```

should set it to default..

have you tried swapping the monitor sections round in xorg.conf?

---

### Post by Cuco3 on 2010-09-16
No I haven't tried switching around the screen sections. I don't know much about Xorg except that it's where all the display settings go. I'm very busy with school and work and I haven't slept so I can't pour too much time into this.

I tried your suggestion and it seemed to do something, but now it's like ATI isn't acknowledging my display settings when I try to change the configuration, like switching the multi-monitor configuration and even disabling the laptop monitor to use the external monitor. In fact, when I click "apply," it just closes the program and doesn't apply anything. Maybe it has something to do w/ permissions because when I go back to the program it shows the previous settings. Also, the ATI catalyst won't let me configure the laptop monitor settings.

One thing I noticed: the "monitors" (gnome-display-properties) options are grayed now when I open it up. it only shows the laptop screen and not the external monitor.

Here's my Xorg.conf:

> Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    Screen         "amdcccle-Screen[1]-1" RightOf "amdcccle-Screen[1]-0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "PreferredMode" "1366x768"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "true"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
    SubSection "Display"
        Virtual   3046 1061
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3046 1061
        Depth     24
    EndSubSection
EndSection


---

### Post by themusicalduck on 2010-09-16
> **Cuco3 said:**
> 
network manager doesn't want to auto log me in to my wifi network


What problem are you having there exactly? Mine was the same, but I fixed it by going to Network Connections, editing the wireless connection and checking the Connect automatically box and the Available to all users box.

---

### Post by Cuco3 on 2010-09-16
> **themusicalduck said:**
> What problem are you having there exactly? Mine was the same, but I fixed it by going to Network Connections, editing the wireless connection and checking the Connect automatically box and the Available to all users box.tried it before, doesn't work, thanks anyway.

---

### Post by SlugSlug on 2010-09-16
It sounds like your ATI program needs to be run as root - am unsure of the command to launch that..

you could try open the program and then
```
ps -ef
```

to see if you can fish it out -- if you can fish it out the try 

```
gksudo  'command'
```

---

