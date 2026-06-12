---
title: "Constant Screen Tearing"
date: 2019-05-30
forum: Desktop Environments
---

### Post by ytterbious on 2019-05-30
I am running 18.04, and I have a Radeon R9 290 video card. On Youtube, in Chrome, no matter what I do, I get screen tearing. What I have done so far (to seemingly no effect) is:

[LIST]
[*]Tried both AMDGPU and Radeon video drivers
[*]Tried both Wayland and Xorg
[*]Turned off Chrome's hardware acceleration feature in the settings,
[*]In CCSM, I went to Utility > Workarounds and turned on ```
Force full screen redraws (buffer swap) on repaint
```, ```
Force complete redraw on initial damage
```, and ```
Don't wait for video sync
```
[*]Added the "TearFree" option with the "on" boolean to
[*]        /etc/X11/xorg.conf,
[*]        /usr/share/X11/xorg.conf.d/10-radeon.conf,
[*]        /usr/share/X11/xorg.conf.d/20-amdgpu.conf, and
[*]        /usr/share/X11/xorg.conf.d/xorg.conf
[/LIST]

All of these came from tutorials I found on Google, promising to forever eliminate screen tearing. However after weeks of this, I've still had no luck.

Any ideas?

---

### Post by arkeo on 2019-12-31
Hi, have you solved the issue?
I always had the same problem (countless HW configs, AMD Ryzen 5 laptop right now on Ubuntu 20.04). The weird part is, (I'm talking about Netflix on Firefox) if I watch a video in a window there's no tearing. If I enter full screen the video becomes unwatchable. Which is the opposite to what happens on Windows on the same HW (I'm guessing it all becomes a DirectWhatever layer, the GPU takes over, no fans spinning, almost negligible battery drain).
Any ideas?

Thanks In Advance...

---

### Post by xadder on 2020-02-28
Just my experience: I switched from xubuntu 19.10 to unbuntu 19.10, and am now also having trouble with youtube videos, but only in full-screen. I can watch other things (eg HBO, BBC iplayer) in full screen without problems, but youtube goes crazy. (xububntu was great for that, but I wanted the better HiDPI support promised by ubuntu-gnome, hence the switch.)

---

