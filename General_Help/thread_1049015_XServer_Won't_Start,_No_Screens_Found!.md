---
title: "XServer Won't Start, No Screens Found!"
date: 2009-01-24
forum: General Help
---

### Post by AndrewRoman on 2009-01-24
Here is what happened, I recently installed 8.10 on my home built computer. Everything went smooth during the install and when GNOME loaded up I was amazed at the new interface. 

However, Ubuntu was not using the right driver for my 2 *Nvidia GeForce 8500GT* Graphics cards which are bridged using SLI.

I was not aware that Ubuntu wasn't using the right driver until I went to add effects to my system which none where being used. Ubuntu recommended me install 177 driver which I couldn't activate. I did some searching on the net and downloaded and installed *EnvyNG* which when it was done running allowed me to activate driver 173. I figured I may need to upgrade the driver to the latest 177 but when my computer rebooted X Server wouldn't load up. Leaving my novice self staring at a command prompt with the following error message.

[B][I]usplash: setting mode 1152x864
usplash: using mode 1024x768

19+0 records in
19+0 records out

kinit:name_to_dev_t(/dev/disk/by-uuid/43bf9faa-oa90-4db2-98a6-28070e4c6bab) = dev(8,21)

kinit:trying to resume from /dev/disk/by-uuid/43bf9faa-oa90-4db2-98a6-28070e4c6bab

bab

kinit:no resume image

doing normal boot

Fatal server error:

no screen found[/I][/B]


Please help me get my GUI working again, I tried Paltalk, but those guys can be kinda "Pompous"

---

### Post by AndrewRoman on 2009-01-27
I ended up fixing it relatively simply, and I'm reposting what I did just in case somebody has the same problem.

The problem I had with my dual "GeForce 8500 GT" cards was that Ubuntu was detecting both of my video cards and neither were set as the primary card. Setting up the BusID linking the monitor to the primary card was all I needed to do and I was greeted with my desktop.

 If anybody has problems with Ubuntu 8.10 spitting out "No Devices Detected" make sure that there xorg file has BusIDs pointing to the monitor.



Section "Device"
    Identifier "Device0"
    BusID "1:0:0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
    EndSubSection
EndSection

---

