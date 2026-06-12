---
title: "XGL vs AIGLX with Beryl"
date: 2007-02-22
forum: Desktop Environments
---

### Post by statictonic on 2007-02-22
I've got a desktop with a nvidia 6800gt video card with nvidia 9746 drivers installed, and the latest version of beryl with AIGLX.(ubuntu 6.10 on both)

I also have a laptop with an ATI x1400 video card and latest binary drivers.  Using XGL and beryl.

Something I noticed is that animations some in particular appear rather choppy on my desktop with AIGLX, while using XGL they are perfectly smooth.

Just curious but am I the only one with this problem, or is it like that for others...  If it is how come?  Just curious.

---

### Post by MasterOfDisaster on 2007-02-23
This used to happen with me, but I added Option  "TripleBuffer" "True" to my xorg.conf, and that smoothed things up a bit.  Also, when beryl-manager is run on startup, I have to restart the window manager to make it run smoothly.

---

### Post by zes on 2007-02-23
hi, i´ve a nvidia 7300 with 9746 too on kubuntu 6.10, one question? wich render platform you use with beryl, AIGLX or Nvidia?, i was using AIGLX and make a "top" command on terminal and discover that xorg. process was eating the cpu, after that i change the render platform to nvidia and was better, xorg process returns to a normal  cpu requirements values.

try it if you want

---

