---
title: "xdmcp weird behaviour - black screens"
date: 2007-11-26
forum: Desktop Environments
---

### Post by bkortleven on 2007-11-26
Hi all,

We have a setup where we installed an Ubuntu 7.04 as a desktop installation, and enabled XDMCP in the gdm configuration files where needed.
The central 'desktop server' is being used through 3 X-aware thinclient (Igel LX series, running an own small linux distro), and working on them is like working on a fullblown computer... you don't see any big difference (except booting and connecting).

Now, I don't have _that_ much experience with XDMCP, but I guess it's something related...
Every x minutes, the screens on all our terminals go black for 2-3 seconds. We have been searching in DPMS and other screensaving settings, and noticed that when one of the users sets his/her screensaver to 10 minutes, the frequency of the 'black screen' goes up... If we put it to for instance 2h, the black screens don't come up at all, or maximum once a day...
To make sure you understand correctly: all screens o black for this 2-3seconds, one after the other (max 1-2seconds between the black screen appearing on the different thinclients)

Is there anybody that has had the same issues or something comparable?
Is this really a XDMCP issue, something Ubuntu/screensaver related, or do we have to look at the implementation of the local X server running on the thinclients?

If someone can explain or narrow down the issue's possible causes, please do! 

Thanks guys!

Bram

---

