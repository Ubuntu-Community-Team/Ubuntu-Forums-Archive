---
title: "X crashes/quit unexpectedly, and respawns on tty8"
date: 2010-08-24
forum: Desktop Environments
---

### Post by aeternitas on 2010-08-24
Just had a strange occurrence...while loading an image in Firefox, X decided to check out on me after a few seconds of hang time, dropping to the normal boot messages that linger on, usually on tty8(see below, shortened a bit), on tty7:

* Starting network interface daemon...                                                                 [OK]
* Speech-dispatcher configured for user sessions...                                               [OK]

And so on.  For a few moments, the system remained rather sluggish; the open terminal session I had on tty1 had a lagtime around 5-7 seconds on key entry, and for a moment the Xorg thread remained present in top.   Shortly thereafter, it was gone.

Within a few minutes (and a failed startx from tty1) later, I cycle through the various terminal options, and tty8 suddenly has a login screen, where it previously would have hosted the above boot messages/checks; logging in, everything seems to be back to par.

However, the logs I've gone over seem to reveal nothing out of the ordinary, nothing to indicate anything went wrong (admittedly, I've only looked over dmesg, syslog, and Xorg.0; not sure if any others might keep anything relevant).  On login under the new X Session, Firefox loaded my tabs and the image on the tab that was my last action before things went haywire was loaded as intended.  

I'm at a loss here, any ideas?

---

