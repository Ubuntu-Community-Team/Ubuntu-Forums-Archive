---
title: "How to sync desktop with vertical refresh"
date: 2009-03-20
forum: Desktop Environments
---

### Post by Milleman on 2009-03-20
Hi,

Is there a way to sync the desktop graphics with the vertical refresh rate? Moving large items around makes the left and right sides to look "jaggared" while moving, just like in Microsoft Windows. On Mac OS-X the desktop graphics is fully in par with the v-sync. So how can I make the same in Ubuntu?

---

### Post by ajgreeny on 2009-03-21
Manually edit your /etc/X11/xorg.conf file and add the info needed.  Here's mine as an example.  I also needed to add the resolution info to get it right on 8.10.

Section "Device"
    Identifier    "Configured Video Device"
EndSection

[B]Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection[/B]

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
     EndSubSection
EndSection

---

### Post by The_Yab974 on 2009-04-30
Hi all!
 
It doesn't work for me. (For the bold section modified i mean.) Should I add subsection precising the available resolution? It the only thing i don't have in my conf file.
 
My config : A64 X2 4600+, Motherboard Asus A8N-SLI Premium, 4Go RAM, GeForce 9800 GX2, Audigy 2 ZS Platinum, Ubuntu 9.04 (AMD64)
 
Ty for help?

---

