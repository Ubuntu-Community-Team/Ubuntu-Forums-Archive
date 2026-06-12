---
title: "screen resolution annoyance"
date: 2008-08-02
forum: Gaming &amp; Leisure
---

### Post by lightstream on 2008-08-02
I installed America's Army and it's running great. However it has real problems going into full screen mode if it's set to the same resolution as my desktop (which is 1152 x 864).

If my desktop is at a different resolution, it can start fullscreen without problems.

I don't know if this is an AA thing or some Hardy setting somewhere.

Anyone have any ideas?

TIA

---

### Post by doorknob60 on 2008-08-03
Possible workaround:

```

#!/bin/bash
xrandr -s 1024x768
americasarmy     <---- replace with correct command
xrandr -s 1152x864

```

Simply, that will lower your resolution, start the game (which will raise resolution), when you close the game, it should lower again, then go back :P If I understood the problem right then it should work though.

---

### Post by lightstream on 2008-08-03
Thanks doorknob60, that certainly works as a workaround and is much less stress than trying to change the res using the applet in Preferences.

It'll certainly do for now but hopefully I'll be able to solve the problem properly sometime!

While using your script, I discovered that it seems that my desktop needs to be set in a higher resolution than America's Army - if the desktop is lower, AA actually crashes taking X with it, and I need to Ctrl-Alt-Backspace to get out of it.

---

