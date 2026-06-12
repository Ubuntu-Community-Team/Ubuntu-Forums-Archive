---
title: "Gridwars  (unable to calculate tex size)"
date: 2010-03-30
forum: Gaming &amp; Leisure
---

### Post by wewantutopia on 2010-03-30
Hello, I'm trying to play gridwars and I keep getting this error when starting via command line.  When starting via launcher nothing happens.  I've tried changing the screen resolution via the config.txt file in ~/.gridwars  to no avail.  The error.txt in the same folder says Can not set graphics mode: Windowed - 800X600

This is windowed or full screen for all the different resolutions up to my monitors resolution (1280x1024)

Anyone else have this issue and get it resolved?

---

### Post by Artanicus on 2011-12-16
Hey!

I know this is a very old post but since I had to find the info the hard way myself, I'll post it here for Future Generations(tm) wanting to partake in the greatness that is Gridwars.

The game will freak out with the error "Unable to calculate tex size" if the Config.txt resolution settings don't match your native resolution. e.g. I'm running dual monitors at 1920x1200 per screen and xrandr gives me the following mode output;

Screen 0: minimum 3840 x 1200, current 3840 x 1200, maximum 3840 x 1200
default connected 3840x1200+0+0 0mm x 0mm
   3840x1200      50.0* 

So, setting the resolution in the config to 3840x1200 lets the game run, assuming you already have libstdc++5. If you want sound, run it through padsp. If you want the original music, play it in schism, it uses SDL for sound so it'll work with pulseaudio. But, take my advice, the original music sucks, bring your own trance. :-)

---

