---
title: "Recognizing new hardware"
date: 2006-01-11
forum: General Help
---

### Post by unclben on 2006-01-11
I installed Breezy on a computer with integrated Intel (Extreme 2) graphics and a Viewsonic VA800 LCD monitor. While Hoary choked and defaulted me to 640x480, Breezy booted me to the correct resolution & refresh rate from the very first time I booted with X.

Recently, however, I switched to a 21" CRT; Breezy didn't appear to notice any difference. My xorg.conf still listed the VA800 and was using the old resolution and refresh rate. I hate to think what would have happened if the switch had happened the other way around and Ubuntu had tried to run my LCD at 1600x1200 @ 85 Hz! Has anyone else had bad experience with Ubuntu recognizing new monitors post-install? How about good experience?

This also brings to mind a broader question ... as good as Ubuntu is at recognizing hardware during installation, how capable is it of accommodating on-the-fly hardware swaps?

---

### Post by invalid on 2006-01-11
To reconfigure your xorg to your new monitor, use this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_orig
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by unclben on 2006-01-12
[QUOTE=invalid]To reconfigure your xorg to your new monitor, use this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_orig
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]
Thanks for the tip, invalid, but I have already fixed the problem by hand-editing xorg.conf. On a related note, though, I tried the reconfigure method once before and found it pretty daunting; I'm somewhat computer savvy, but I remember just scratching my head after reading several of the questions it asked.

---

### Post by invalid on 2006-01-13
[QUOTE=unclben]Thanks for the tip, invalid, but I have already fixed the problem by hand-editing xorg.conf. On a related note, though, I tried the reconfigure method once before and found it pretty daunting; I'm somewhat computer savvy, but I remember just scratching my head after reading several of the questions it asked.[/QUOTE]
Glad you got it worked out.

I will agree, and especially for newer users, that the process can be a bit rough. Most screens will attempt to auto detect the best value, so that you can just hit the enter key. There are a couple, though, that you sort of need to know what you're doing. Perhaps someday it will be updated to be slightly more user friendly.

Cheers

---

