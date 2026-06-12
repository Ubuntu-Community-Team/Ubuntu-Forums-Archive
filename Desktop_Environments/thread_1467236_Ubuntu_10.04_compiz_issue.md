---
title: "Ubuntu 10.04 compiz issue"
date: 2010-04-30
forum: Desktop Environments
---

### Post by MadDawg010 on 2010-04-30
Alright, before I upgraded to 10.04 (from 9.10), compiz was working fine and smoothly. After the upgrade, I found that my window borders were missing, and it turned out that the Visual Effects were disabled.

The issue I'm having here is that ccsm or the window manager or whatever does not seem to want to remember any changes when I reboot. I have to reenable the Visual Effects and make all my settings in ccsm each time I boot. On top of that, the environment starts to bog down (sometimes gdm kills itself and I have to log in again) after a certain amount of stress is put on the computer, which did not happen in 9.10. Any suggestions?

Computer specs:

Intel Celeron M 1.6GHz
IBM ThinkPad R51e
2GB RAM (maxed)
ATI RADEON XPRESS 200M Series

I also want to add that when I type 'compiz' into a terminal I get this:

> WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!


And, when I do a Ctrl+C to terminate the command, I end up resetting the ccsm and Visual Effects to default.

---

### Post by Xanthomryr on 2010-04-30
Same Problem here. :( 
After reboot the desktop effects are gone, so are my window boarders. I have to enable them everytime I reboot.

System specs:

Athlon 64 X2 3800+
Asus A8N-E Mainboard
2 GB Ram
Nvidia GeForce 6600

---

### Post by MadDawg010 on 2010-04-30
Adding a start-up entry with this command (which I found in this thread: [http://ubuntuforums.org/showthread.php?t=1456605&page=2](http://ubuntuforums.org/showthread.php?t=1456605&page=2)) seems to have resolved the issue. The command needed is as follows:
```
/usr/bin/compiz
```

I'm assuming the instability may just be because of my outdated hardware.

---

### Post by Xanthomryr on 2010-04-30
Yeah, I saw that thread too, but this looks more like a workaround to me because I didn't have (needed) this entry before I upgraded to Lucid.

And '/usr/bin/compiz-decorator' is also enterded in the Window Decoration Plugin in CCSM :confused:

---

### Post by ias on 2010-05-08
Same problem on my eee pc 1005HA. Hope a solution will be included in auto-updates soon.

---

