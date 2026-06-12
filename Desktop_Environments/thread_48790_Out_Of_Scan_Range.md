---
title: "Out Of Scan Range"
date: 2005-07-13
forum: Desktop Environments
---

### Post by Tinknocker on 2005-07-13
OS seems to have been installed. After booting monitor screen goes blank, info box appears stating: monitor is working, out of scan range,change settings in pc. Have rebooted thru recovery mode after which I have used; sudo dpkg-reconfigure xserver-xorg. All settings seem to be correct I have tweaked same but still get the same info box and nothing else.  I am new to LINUX and am running it on a spare machine to try it. The version is HOARY 5.04, the comp. is DELL 2400 w/integrated card Intel 845G, monitor is DELL M992 CRT. The info box also shows 29.2 KHg and 
55Hg.     Any suggestions?

---

### Post by maruchan on 2005-07-13
I think you need to edit your /etc/apt/xorg.conf file and add a little something that goes like this:
> Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Dell M992"
DisplaySize 350 260
HorizSync 30.0 - 96.0
VertRefresh 50.0 - 160.0
Option "dpms"
EndSection

...or at least change the HorizSync and VertRefresh numbers to match that. I'm not sure if the configuration utility lets you change those numbers; maybe it does.

This is more dicey, but here's more from this guy's xorg.conf. Sounds like he may have the same system as you. Do you have an NVIDIA GeForce 4 MX?

> Section "Device"
Identifier "Videocard0"
Driver "nv"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce 4 MX (generic)"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 16
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection


Here's the reference (french):

[http://www.fedora-france.org/modules/newbb/viewtopic.php?topic_id=1243&forum=6&post_id=6531](http://www.fedora-france.org/modules/newbb/viewtopic.php?topic_id=1243&forum=6&post_id=6531)

Google search strategy:
DELL M992 xorg.conf

---

