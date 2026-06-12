---
title: "Monitor stays on black screen for 10 minutes before turning off"
date: 2017-03-23
forum: Desktop Environments
---

### Post by Segnale007 on 2017-03-23
Hello Team,

thank you for having me here today.

I have installed Ubuntu 16.04 LTS on my Lenovo ThinkPad x230 doing a minimal install with just full Mate Desktop, rich fonts library, SAMBA and OpenSSH Server.

Everything is working as it should be, apart form a _**small**_ important detail; when screensaver kicks in and I have it set on "Blank Screen" the monitor backlight led stay on for 10 minutes idling before ultimately turning off.

From what I understood what is causing the monitor backlight led to stay on for 10 minutes after screensaver has kicked in is actually Xorg (I could be wrong though).

What I did is I created a backup of the default auto generated [COLOR=#008000]Xorg.conf[/COLOR] and created a [COLOR=#008000]10-monitor.con config [/COLOR]file in** /usr/share/X11/xorg.conf.d/ **.

```

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option "DPMS" "false"
EndSection
 
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        Option "BlankTime"  "0"
        Option "StandbyTime" "0"
        Option "SuspendTime" "0"
        Option "OffTime" "0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

I tried with both DPMS true and false but I get the same result in [COLOR=#008000]/var/log/Xorg.0.log[/COLOR]

```

[     9.304] (WW) intel(0): Option "BlankTime" is not used
[     9.304] (WW) intel(0): Option "StandbyTime" is not used
[     9.304] (WW) intel(0): Option "SuspendTime" is not used
[     9.304] (WW) intel(0): Option "OffTime" is not used

```

Here is the the auto-generated unaltered [COLOR=#008000]Xorg.conf[/COLOR] file [https://paste.ubuntu.com/24232916/](https://paste.ubuntu.com/24232916/) .

[COLOR=#ff0000]What I want to achieve is;[/COLOR] I don't want any screensaver pictures thing, all I want is that after a certain period of idle time the monitor to turn off and automatically lock the user session. I am not sure if this can be achieved without screensaver thing. 

Right now I have power management set to dim the brightness screen after 7 minutes of idle time, while screensaver should lock the session after 30 minutes idle in AC and 10 minutes on battery. 

Thank you for taking the time to read and I apologize for the colored texts :) .

---

### Post by Segnale007 on 2017-03-23
Bump

---

