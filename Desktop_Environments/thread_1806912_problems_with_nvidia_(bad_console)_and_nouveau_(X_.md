---
title: "problems with nvidia (bad console) and nouveau (X won't run)"
date: 2011-07-18
forum: Desktop Environments
---

### Post by Skaperen on 2011-07-18
With the nvidia driver in use, the text console is nearly unusuable.  The font is extremely tiny and the video sync boundaries exceed the monitor capability.  But it gets worse.  About 1 out of 3 times, when switching back to X, the video has become corrupted and all that can be seen is a "blit mess" (random bits on the screen).  A few times the kernel has crashed, too (I see nothing, the machine is locked hard, and even pings don't answer anymore).  Basically, the nvidia driver just does text console all wrong.  And I see that in other distros, too.

Under Slackware 13.37 upgraded to the 2.6.38.X (where X is 4 or 7) kernel, the nouveau driver works fine in both text console and X.  However, when I try to use the nouveau driver in Ubuntu 11.04 (by blacklisting nvidia and unblacklisting nouveau), the text console starts working perfectly, but X just won't run at all.  Manually running startx gives messages about being unable to load the "nvidia" and "nv" drivers saying they are not found (but does not say where it is expecting to see them).  Since X works fine in Slackware (don't know if it's the same version), I suspect possibly some configuration issue.  But I cannot find a configuration file that is referencing nvidia.

Anyone know how to get X to work with the "nouveau" driver under Ubuntu 11.04?  The kernel version looks one that should work.

---

### Post by papibe on 2011-08-18
That has similar symptoms to a problem that I had with a card/display with a corrupted EDID. It gave me problems from instability to incorrect resolutions. Read [this]("http://blog.freshnewpage.com/") in order to check if your EDID is correct (or at least discard that problem).

Just a thought,
Regards.

---

