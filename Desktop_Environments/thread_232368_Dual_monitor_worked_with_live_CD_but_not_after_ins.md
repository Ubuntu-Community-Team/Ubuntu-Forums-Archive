---
title: "Dual monitor worked with live CD but not after installation"
date: 2006-08-08
forum: Desktop Environments
---

### Post by lorre on 2006-08-08
I can't get my radeon 7000 to detect my screen when using DVI. When connecting using VGA all goes well. But with DVI I get a black screen and Xorg.0.log saying:

(II) RADEON(0): Primary:
 Monitor   -- TMDS
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=19600
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)

What can I do to enable my second monitor using DVI with the Radeon 7000?

---

### Post by computergroove on 2006-08-08
If it worked with the live cd then just copy the contents of the /etc/X11/xorg.conf from your live cd to your /etc/X11/xorg.conf and restart x. If you want to install newer drivers then just try it. You can always restore your old xorg.conf  - sudo cp /etc/X11/(your xorg.conf_backup...file) /etc/X11/xorg.conf

---

### Post by lorre on 2006-08-09
Thnx, installing the drivers did help. It also helped me to get rid of the clone mode. No I am in some kind of twinview where I cannot drag a window to the other screen, instead I have to start the program in the other screen. It's also not possible to start firefox in both screens because it will complain in the second screen that is already started.

Is it possible to drag windows accross screens?

---

### Post by lorre on 2006-08-09
Never mind, I found the following solution in this forum:

"SOLVED: A friend of mine pointed out that I need to put Option "Xinerama" in the ServerLayout section, it works fine now."

---

