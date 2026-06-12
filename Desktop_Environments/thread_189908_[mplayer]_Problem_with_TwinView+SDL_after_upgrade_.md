---
title: "[mplayer] Problem with TwinView+SDL after upgrade to 6.06"
date: 2006-06-05
forum: Desktop Environments
---

### Post by 123dfdfg43 on 2006-06-05
Hi,

I've been using _twinview_ with my _nVidia_ card and [COLOR="DimGray"]_**mplayer**_[/COLOR] for 3 years without problems: with _SDL_ driver mplayer was capable to find right settings to work fine with my TV.
Yesterday I did the upgrade to _[COLOR="DimGray"]Ubuntu 6.06 TLS[/COLOR]_, and mplayer doesn't find TV anymore. I'm sure the problem depends on mplayer/SDL and not Xorg: if I swich resolution by hand, Xorg finds TV, but mplayer doesn't.

What can I do to fix it?

Here's **xorg** file, that had worked till yesterday:
[INDENT][http://aballatore.altervista.org/files/tmp/xorg.conf](http://aballatore.altervista.org/files/tmp/xorg.conf)[/INDENT]

Here's **mplayer** config file:
[INDENT][http://aballatore.altervista.org/files/tmp/config](http://aballatore.altervista.org/files/tmp/config)[/INDENT]

Here's the packages version:

* Linux 2.6.15-23-386 #1 PREEMPT
* mplayer-k7      0.99+1.0pre7try2+cvs20060117-0ubuntu8
*  nvidia-glx                             1.0.8762+2.6.15.11-1  NVIDIA
binary XFree86 4.x/X.Org driver
* nvidia-kernel-common                   20051028+1  NVIDIA binary
kernel module common files
* libsdl1.2debian                        1.2.9-0.0ubuntu2  Simple
DirectMedia Layer

Bye and thank you,
Andrea

---

