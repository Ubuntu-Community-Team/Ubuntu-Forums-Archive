---
title: "Multiple displays, unity greeter, xorg.conf!"
date: 2013-04-09
forum: Desktop Environments
---

### Post by cotigao on 2013-04-09
Hi,

Can anybody explain me which one has higher precedence?  xorg.conf or the "Displays" utility (top right corner in panel, which I  guess is per user setting, stored in gconf?).
Also what mode does the unity-greeter work (if there are multiple displays). Seems to me it always selects Mirror mode.

I  see that the unity greeter picks the (perhaps correct) resolution ("modes" section) from  the xorg.conf file but ignores the "Server Layout" section (my xorg.conf has vertical  layout specified). Instead, it goes into mirror mode. The values in  xorg.conf file are well within the maximum virtual size.

Next,  after I login, I see that the displays (HDMI-1, VGA-1) gets configured to whatever I had  set through the "Displays" utility (before logging out last time)  and  not as per the xorg.conf file. Isn't xorg.conf system-wide ? and is  meant to override all the users' settings (done via "Displays")?

I am confused! Here's my xorg.conf file.



Section "ServerLayout"
   Identifier "Default"
   Screen 0 "VGA-1" 0 0 
   Screen 1 "HDMI-1" below "VGA-1"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC LCD1970NXp"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
EndSection

Section "Screen"
   Identifier "VGA-1"
   Device "Device0"
   SubSection "Display"
     Modes "800x600"
   EndSubSection
EndSection



Section "Screen"
   Identifier "HDMI-1"
   Device "Device0"
   SubSection "Display"
     Modes "800x600"
   EndSubSection
EndSection

---

### Post by jakobwilm on 2013-05-17
Bump! I am facing the same problems. Some or all of my xorg.conf configurations seem to be ignored. Is there any way of disabling Unity/lighdm control of screen configurations?

---

