---
title: "problem with AMD fglrx and Xorg settings"
date: 2012-06-05
forum: Desktop Environments
---

### Post by lunemec on 2012-06-05
Hi guys, 

I found a bit of a problem, when I installed proprietary drivers (I know they suck but without them system is sluggish) and I found out that my system freezes when trying to login with dual monitor config, I have Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] GPU and I set up my X via amdcccle.

I have 2 monitors one VGA and one HDMI, it works with open source driver but this should work as well..

I found out that when I unplug VGA monitor before boot, system will boot properly and when I plug it again after boot on live system it does exactly what I want! but I'm not able to leave both of them plugged in, I get login screen and after login i see black screen with pointer and PC is frozen, and have to hard reboot...

here is my Xorg.conf
```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
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
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1600x900"
    Option        "TargetRefresh" "60"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3280 1680
        Depth     24
    EndSubSection
EndSection
```Thanx for any help :)

---

### Post by typhoon_tip on 2012-06-05
Instead of hard reboot, try CTRL+ALT+F1 and see if the system is responding or not. If yes, type your username then enter, your password then enter.

After that:
```
sudo reboot
```

... should reboot the system safely.

By the way, the entire test is to see if XORG is frozen or the system is in an "unfamiliar" state.

---

### Post by lunemec on 2012-06-05
No it doesnt work, keyboard is frozen, num lock will not change diode state.. :D 

Weird is that when I unplug VGA before boot and then replug it again it works as it should...

---

### Post by typhoon_tip on 2012-06-05
Have you installed the drivers with Additional Drivers or from ATI ?

If the first one, I strongly suggest you to install the one from AMD website, is much updated.

To do so, follow very very diligently the instructions in the below link, on how to properly **purge the driver** before **installing** the new one ! Follow all the steps, do not skip anyone !
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

You are using Ubuntu 12.04, rite ?

---

### Post by lunemec on 2012-06-06
Ok, I'll try it, thanks, and I'm using latest ubuntu, but I have trust issues with amd's drivers, before I had debian with i3wm and AMD driver ****** up my system completely, windows were lagging, it was terrible, so I went back to the open source driver, because fglrx didn't work and installer from AMD site was even worst

I'll try it when I'll have time to play with xorg.. thx

---

### Post by lunemec on 2012-06-08
Alright, I followed these steps precisely
but no avail

it doesnt work, system freezes when I try to configure it using xrandr

when you change something with xrandr, freeze

so **** IT..

disconnected VGA and now working with 1 lcd... 

AMD really can make you use windows... or they can make you not want to use linux :D

---

