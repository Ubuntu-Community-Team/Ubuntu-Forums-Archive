---
title: "ATI Dual Monitor Left/Right"
date: 2011-01-21
forum: Desktop Environments
---

### Post by Cuco3 on 2011-01-21
Ubuntu 10.04

I have the ATI proprietary drivers installed. I have a dual monitor set  up: laptop on my left, and LCD on the right. I have the LCD set up as  the main screen, but I want to be able to move my mouse to the left onto  the other screen. As of right now, I have to go to the right in order  to get on to the other screen.

The ATI GUI tool, even w/ Administrative privileges, does not apply the  changes I want it to. I can't even enable somethings like Xinerama.  Weird.

Here's my xorg.conf

```
Section "ServerLayout"
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
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1366x768"
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
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3046 3046
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Here's a weird thing also: I can only enable/disable monitors  using the default "Monitors" tool. And when I arrange the monitors  there, it still doesn't apply the changes.

---

### Post by Cuco3 on 2011-01-21
Any1 please?

---

### Post by Cuco3 on 2011-01-21
please?

---

### Post by gerowen on 2011-01-21
I installed the ATI proprietary drivers from synaptic, but when I hook my laptop up to my TV for playing Nintendo 64 or something I don't even use it.  I just use the "System -> Preferences -> Monitors" thing.  You can drag the little diagram boxes around in that to identify the setup of your screens, hit apply and it configures your display accordingly.  I had to use it the first time to tell it that the TV was to the right of the laptop and that I did not want them mirrored.

---

### Post by gerowen on 2011-01-21
By the way, you may have to log out and back in after applying changes for them to take effect.  A lot of times, if it's the first time you've hooked up a particular secondary monitor, you'll have to re-log (which in effect restarts X) so the settings can be written to the configuration file.  Then you should be able to plug-and-play that particular monitor in the future.

---

### Post by Cuco3 on 2011-01-21
> **gerowen said:**
> I installed the ATI proprietary drivers from synaptic, but when I hook my laptop up to my TV for playing Nintendo 64 or something I don't even use it.  I just use the "System -> Preferences -> Monitors" thing.  You can drag the little diagram boxes around in that to identify the setup of your screens, hit apply and it configures your display accordingly.  I had to use it the first time to tell it that the TV was to the right of the laptop and that I did not want them mirrored.I have tried it that way. Unfortunately, it moves the actual desktop (ie startmenu) to the left and makes my LCD the secondary monitor. What I need it to do is keep the LCD monitor as main monitor (right) and make the Laptop (left) the secondary monitor. I want to be able to move the mouse over to the left side of the screen to switch from Main to Secondary monitor. Thanks anyway.

Any1 else? Please?

---

### Post by Krytarik on 2011-01-21
```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
[COLOR=Red]     Screen      1  "amdcccle-Screen[1]-1" RightOf "amdcccle-Screen[1]-0"    # add this
[/COLOR]EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
[COLOR=Red]     Option        "Xinerama" "off"                  # set this to "on"
[/COLOR]EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
[COLOR=Red]     Option        "Position" "0 0"                    # isn't necessary in this setup
[/COLOR]    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
[COLOR=Red]     Option        "Position" "1680 0"[/COLOR][COLOR=Red]               # isn't necessary in this setup[/COLOR]
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1366x768"
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
[COLOR=Red]     Option        "Monitor-LVDS" "0-LVDS"    # remove this one
[/COLOR]    BusID       "PCI:1:5:0"
[COLOR=Red]    Screen      0                                    # add this
[/COLOR] EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
[COLOR=Red]         Virtual   3046 3046                 # may have to removed
[/COLOR]        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Since you have not said which one is the LCD and which one the laptop screen, it may be the other way around. I've assumed it from the specified positioning.

[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

---

### Post by MashUseLinux on 2012-07-13
Any one got any solution?
me too got the same problem on 12.04, i keep my extra monitor on the left and laptop on the right. So i want to move the mouse smoothly from laptop to extra monitor moving mouse towards left, as for now its getting when moving towards right only, thats weired..

---

### Post by wildmanne39 on 2012-07-13
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

