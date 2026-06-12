---
title: "fceux skipping frames"
date: 2009-01-09
forum: Gaming &amp; Leisure
---

### Post by ProcyonSJJ on 2009-01-09
Hello.  I've just recently downloaded and compiled fceux and gfceux.  Everything is working fine, except that I am clearly not getting 60FPS, even though the frameskip is set to 0.  By comparison, NES emulation in Mednafen is running at a smooth FPS. I don't know what could be causing the disparity.  I have OpenGL rendering checked, and this effect occurs whether I'm in full screen or not.  Sound settings are default, and I even added "--frameskip 0" just to be sure.  I can speed up the emulation to something ridiculous like %800, but at %100, the animation slightly lurchy.  I'm running Ubuntu 8.10 on a Toshiba Qosmio X305 Q701, so processing power is not an issue.  Any help would be greatly appreciated.  Thanks

Procyon

---

### Post by disturbedite on 2009-01-10
i'm entirely clear on the effect you're having, but, if vsync is enabled try disabling it. if it is disabled try enabling it.

---

### Post by ProcyonSJJ on 2009-01-10
I looked at the .cfg file, the command line, and the fceux online documentation.  There is no option to set the vsync on or off.  I am positive that the emulator is skipping frames despite the fact that I specify -fs 0.  When I run at full speed in Super Mario Bros. 3, Mario appears to float over the ground with no animation.  Either this is a legitimate bug in the emulation, or I something went very wrong when I ran scons.

Procyon

---

