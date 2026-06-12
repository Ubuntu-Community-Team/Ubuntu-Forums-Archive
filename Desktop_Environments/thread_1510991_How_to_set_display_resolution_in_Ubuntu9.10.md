---
title: "How to set display resolution in Ubuntu9.10"
date: 2010-06-16
forum: Desktop Environments
---

### Post by pravindra.kumar on 2010-06-16
Hi,
I have installed Ubuntu9.10 Desktop but i am facing problem with display resolution which is by default set for 800x600 but i need at least 1024x768.
I tried it by doing following steps:-
(1) System > Preferences > Monitor but did not find entry for more than 800x600.
(2) Used xrandr but not succeed.
(3) Tried to find xorg.conf but not found in /etc/X11/

Please guide how to do the same.

Regards,
Pravindra

---

### Post by rajn on 2010-06-16
> **pravindra.kumar said:**
> Hi,
I have installed Ubuntu9.10 Desktop but i am facing problem with display resolution which is by default set for 800x600 but i need at least 1024x768.
I tried it by doing following steps:-
(1) System > Preferences > Monitor but did not find entry for more than 800x600.
(2) Used xrandr but not succeed.
(3) Tried to find xorg.conf but not found in /etc/X11/

Please guide how to do the same.

Regards,
Pravindra


Looks like your monitor is not being recognized. Do you know what is your graphics chip?
Nvidia, Intel etc....you can find that by doing lspci.
Xorg.conf is not by default provided with Ubuntu. You will have to generate it.

I suggest [http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466](http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466) and links therein.

Basically you will have to do this
**$sudo gedit /etc/X11/xorg.conf**

This will open a blank document.

I am giving as an example below what you have to copy paste or write to this file (this is for intel chip) and then save.

For your chip you will have to find specifications. If you have run Xrandr, it may already may have given you the specifics. 
Most important lines are in **bold.** The rest really do not matter what you "name" them i.e., instead of 'configured device' you may actually call it 'xyz' but make sure that name is maintained all over in this file.
The most important lines are the sync rates. You may opt out by commenting useedid, reduceblanking or renderaccel. Those may not be an issue. Once you figure out hsync and vsynch for your graphics card then you can play with the rest by inserting them one at a time.

There are ways to figure out these numbers. Best is google and find out from the vendors. It may be listed.

Save and reboot. If you get a garbled screen do cntrl+alt+F1 and this will open another terminal.
remove xorg
**sudo rm /etc/X11/xorg.conf**

reboot and again create xorg with new parameters. Keep doing this till it works. Best is from the links maybe you will find someone who has figured this out for your card. I know it sounds discouraging but believe me you will find a solution if you look carefully.
Many people have this problem





Section "Device"
Identifier "Configured Video Device"
Option "RenderAccel" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
[B]HorizSync 31.5 - 50.0
VertRefresh 40-90[/B]
Option "UseEdidFreqs" "1"
Option "ReducedBlanking"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
[B]DefaultDepth 24

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection[/B]

Good luck

---

### Post by pravindra.kumar on 2010-06-17
Thanks Dear.

---

### Post by Chame_Wizard on 2010-06-17
```
sudo xrandr -S set display-resolution
```

---

