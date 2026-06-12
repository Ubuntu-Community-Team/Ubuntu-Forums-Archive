---
title: "screen resolution"
date: 2008-12-31
forum: General Help
---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
maximum seems to be 800by600.

I'd prefer it to be the 1024by268 that the screen previously ran at. I'm guessing the answer is likely to be get a graphics card, (based on the few results that seemed to match when I searched)

from what I remember this PC used to run at 1024/768 when it was on xp. (so using the same onboard graphics)

---

### Post by damis648 on 2008-12-31
What graphics card do you have, and have you tried enabling the driver from System>Administration>Hardware Drivers?

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
its the built in 1 on the motherboard.

just downloading the Driver for it now (nvidia)

will let you know how it gets on

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
just installed the recommended nvidia driver, for it to bugger up the screen,

looks like I got a zebra sitting on it....

---

### Post by linux_tech on 2008-12-31
If you type:  ```
xrandr
```
(in the terminal) what are the available resolutions?

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
Screen 0: Minimum 320 x 240, Maximum 800 x 600
Default connected 800x600+0+0 0mm x 0mm
800x600 60.0* 56.0
640x480 60.0
400x300 60.0  56.0
320x240 60.0

just managed to deactivate the driver, as it buggers up the display something chronic

---

### Post by Geemonster on 2008-12-31
I noticed this,my XP resolution is 1024x768,whereas my ubuntu is 800 and something x800and something,VLC plays nice,but it would be nice to have the option of 1024x768.

---

### Post by linux_tech on 2008-12-31
if you previously had 1024x768 and now don't have it, it probably means that a change has changed the xorg.conf.  If you look in /etc/X11
there are usually a few xorg files. You can copy one of the others to replace xorg.conf and get your old resolution back. MAke a copy of the current xorg anyway.
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
> **linux_tech said:**
> if you previously had 1024x768 and now don't have it, it probably means that a change has changed the xorg.conf.  If you look in /etc/X11
there are usually a few xorg files. You can copy one of the others to replace xorg.conf and get your old resolution back. MAke a copy of the current xorg anyway.
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

didnt have it on this PC (only just got ubuntu to run today)when the monitor was running on the current pc (the one I'm typing on) it was run at 1024/768. I moved it over to the other machine once I got a tft to replace it.

however ubuntu only shows up to 800/600.

is it worth modifying it along the lines suggested here
[http://ubuntuforums.org/showthread.php?t=24923](http://ubuntuforums.org/showthread.php?t=24923)

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
just come across something in the release notes for 8.10.

> nVidia "legacy" video support

the 71 and 96 series of proprietary drivers, as provided by the nvidia-legacy and nvidia-glx packages in ubuntu 8.04 LTD, are not compatible with the X.Org included in Ubuntu 8.10

the 96 series is what ubuntu recommends, stating "tested by the ubuntu developers" but when I tried it it turns into black and white stripes across the screen

---

### Post by PsYcHoTiC_MaDmAn on 2009-01-05
bought a cheap AGP card (ATI 9550) (£8 inc postage) shoved it in, worked perfectly.

mark as solved

---

