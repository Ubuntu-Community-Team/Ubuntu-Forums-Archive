---
title: "Ubuntu 8.04 - Compiz running slow - Worked before"
date: 2009-02-25
forum: Desktop Environments
---

### Post by josh6847 on 2009-02-25
I was trying to get extended monitor to work, and basically jacked up my settings. Luckily, I had backed up my xorg.conf file before I changed anything, but after I switched back to the original file, compiz ran very slow. I tried a number of things and no matter what, the rendering is crappy. This all worked before, so I am unsure what happened. Without special effects on, the system runs fine. Just need some things for better development environment... 

This is what I tried so far:
- set SKIP_CHECKS=yes
- removed xserver-xgl
- ran compiz-check program (everything passes)

Heres the relevant information in xorg.conf (the original):
Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "LVDSBiosNativeMode" "false"
        Option          "GARTSize" "64"
        Option          "AGPSize" "64"
        Option          "AGPMode" "4"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode" "8"
        Option          "AGPFastWrite" "True"
        Option          "EnablePageFlip" "true"
        Option          "EnableDepthMoves" "true"
        Option          "UseInternalAGPGART" "no"
        Option          "BackingStore" "on"
        Option          "UseInternalAGPGART" "no"
        Option          "DMAForXv" "true"
        Option          "AccelMethod" "XAA"
        Option          "ColorTiling" "on"
        Option          "AccelDFS" "true"
        Option          "TripleBuffer" "true"
        Option          "DynamicClocks" "on"
EndSection


Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

I even tried setting the driver to "ati" and "fglrx" as well. Any help would be great.

Thanks!

Josh R

---

### Post by sgissinger on 2009-03-07
I'm a t42 user (also on ati7500), i got the exact same problem. 
The thing is our 7500 got blacklisted after the release of hardy, which means they're not developing restricted drivers anymore. A pity, compiz fusion was SO good looking! I tried asking question on Ubuntu launchpad ([https://answers.launchpad.net/ubuntu/+question/31643]("https://answers.launchpad.net/ubuntu/+question/31643")), but nobody answered... The thing is, as you can see at the end of the launchpad thread, you could try the SKIP_CHECK mehod or even try installing fusion-icon (it's in the default repos, install it through apt-get) but I think you would get the same problem (I did) : very slow and bad looking compiz effects. 
But fortunately, I discovered compiz fusion was not the only way to get a nice looking desktop : I installed xcompmgr to get the transparency enabled in cairo-dock, I also installed Ubuntu Studio, very simple, very nice and wallpaper tray which allows you to display randomly tons of wallpaper you placed in a certain folder. If you're looking for nice wallpapers, I strongly recommend you [Interface Lift]("http://interfacelift.com/wallpaper_beta/downloads/date/any/index1.html"). 

Hope this helps!

---

