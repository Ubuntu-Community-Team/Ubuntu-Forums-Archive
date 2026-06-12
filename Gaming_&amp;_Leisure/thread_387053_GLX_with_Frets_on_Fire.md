---
title: "GLX with Frets on Fire"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by hardyn on 2007-03-17
```

open /dev/sequencer: No such file or directory
open /dev/sequencer: No such file or directory
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 64, in ?
  File "src/GameEngine.py", line 154, in __init__
  File "src/Video.py", line 68, in setMode
pygame.error: Couldn't find matching GLX visual

```

What can anybody make of this?
I do have GLX... i am running the Nvidia Binary Drivers.

thanks.



*** update ***

All fixed, i did not realize the that nvidia-settings had to be run using gksudo... makes sense now... oops.

---

### Post by bunjiro on 2007-03-23
I'm having the same problem... how did you fix this? By simply running nvidia-settings? I used Envy to set up my Nvidia card, and xorg.conf looks correct to me. All other games use glx just fine, and running nvidia-settings doesn't help.

---

