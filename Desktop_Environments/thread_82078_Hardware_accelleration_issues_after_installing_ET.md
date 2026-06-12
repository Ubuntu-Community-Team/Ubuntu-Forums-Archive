---
title: "Hardware accelleration issues after installing ET"
date: 2005-10-25
forum: Desktop Environments
---

### Post by DuplexEmotions on 2005-10-25
Howdy,
I was trying to install Enemy Territory on my laptop (Inspiron 1150) and it didn't work properly. Now it seems that I don't get any hardware accelleration anymore, not even on tests like glxgears. Other programs using 3d rendering lag or break entirely, my screensaver doesn't even get a decent framerate anymore.

Is there any way I can restore my video settings back to their original configuration? I don't have much linux experience so I'd appreciate getting the simple version of any answer.

Thanks a lot,
John

here's the crash log from when I started up tuxkart. The game menu came up but it crashed as soon as I tried to start a race:
```

Data files will be fetched from: '/usr/share/games/tuxkart'
PW: This is an *INDIRECT* rendering context.PW: That may be bad for performance.Data files will be fetched from: '.'


   TUXEDO T. PENGUIN stars in TUXKART!
               by Steve and Oliver Baker
                 <sjbaker1@airmail.net>
                  http://tuxkart.sourceforge.net


Kart 0 == 'tuxkart.ac'
Kart 1 == 'geekokart.ac'
Kart 2 == 'bsodkart.ac'
Kart 3 == 'gownkart.ac'
READY TO RACE!!
tuxkart: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
Aborted

```

---

