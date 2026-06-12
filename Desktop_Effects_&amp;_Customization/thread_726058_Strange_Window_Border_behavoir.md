---
title: "Strange Window Border behavoir"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by MichaelBaron on 2008-03-16
While using Ubuntu 7.10 AMD64 with the preinstalled compiz-fusion package
and newer NVidia drivers (the 169.x series),
from time to time I experience strange window border behavior, like shown in the attached picture.

It would be glad, if someone had a solution to this very annoying problem.

---

### Post by lian1238 on 2008-03-16
What window decorator do you use? (like, Emerald? or you didn't install anything?)

Try running ```
gtk-window-decorator --replace
```
or ```
emerald --replace
```
if you maybe use emerald.

Does it fix the problem? If so, you might just put a launcher on your panel with the command that works, if the problem doesn't happen that often.

---

### Post by coderdb on 2008-03-17
I'm having the exact same problem (HP dv8395 laptop, NVIDIA Go 7600): the title bar either looks like the screenshot from MichaelBaron, goes completely (like in [this thread]("http://ubuntuforums.org/showthread.php?t=517654"), just running it with what's "in the box" with Gutsy) or sort've "half disappears" at a weird angle. Installing the 169.12 driver from NVIDIA helped a bit, and now it doesn't happen *quite* so often, but it's still there.

Any help would be much appreciated!

---

### Post by Therion on 2008-03-17
I'm going to post this because it MIGHT be of help to someone else.  I've found that starting Compiz, by default, also starts Emerald.  Emerald, for me, was the cause of all sorts of window-decorations problems.  By turning it off,the problems went away only to return, however, when I rebooted because Emerald would restart with Compiz at boot.  I didn't WANT Emerald doing anything, personally.  Compiz yes, Emerald no.   

Entering the following into the Terminal will prevent Emerald from starting up with Compiz, which is what solved my problem with disappearing window-decorations and such.  Obviously you don't want do this if you use Emerald for theming your windows:
```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```

---

### Post by coderdb on 2008-03-17
Just tried that little script of yours Therion...it seems to have improved it a lot, but it still happens from time to time. At least to the point where it's not really annoying any more.

---

### Post by Therion on 2008-03-18
> **coderdb said:**
> Just tried that little script of yours Therion...it seems to have improved it a lot, but it still happens from time to time. At least to the point where it's not really annoying any more.
Well I'm glad it helped, but I can't take credit for the script.  I got that after beating my head against a wall for I don't know how long and then finally got help on a Compiz-Fusion forum.  That's where I got that particular line of code.

Something else to try would be the Windows Decoration plugin under Compiz.  Try turning it on if it's off, or off if it's on.  One last suggestion (I told you I've been down this path...) Install this [Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch).  Use it to turn OFF Compiz (which will put you into Metacity) change your theme, or do whatever you need to do, and then use it to restart Compiz.  That MIGHT help.

---

### Post by coderdb on 2008-03-19
I tried turning off the Window Decorations part of Compiz, but then the window borders vanish. No titles, close/maximise/minimise buttons or anything. Even after a restart.

I have a feeling it's something to with my laptop/graphics card: GeForce Go 7600. Looking around the forums, loads of people seem to be having problems with them. So maybe it's something with NVIDIA more than Compiz or Ubuntu?

---

### Post by MichaelBaron on 2008-03-22
One "solution" is installing the NVIDIA driver for legacy graphics adaptors (version 96.43.05 or so).

---

### Post by BKonkle on 2008-03-22
I'm having the same issue.  I've attached a screenshot.  I'm running Hardy with an Nvidia GeForce 7300 GT, without Emerald installed.  In addition, I'm having this issue when windows are maximized  [http://www.youtube.com/watch?v=ci4ewC2Pdnc](http://www.youtube.com/watch?v=ci4ewC2Pdnc)

---

### Post by coderdb on 2008-03-22
After installing Emerald, everything seems to be OK (touch wood). And it did only happen with maximised windows.

---

### Post by BKonkle on 2008-03-24
I've heard of some other people having difficulty with Emerald.  Have you had any issues so far?

---

### Post by coderdb on 2008-03-25
I've had no problems. Once today I had to restart compiz because all the window decorations went for no apparent reason, but that's the only thing so far.

---

