---
title: "Plausibility of a script to switch between radeon and fglrx"
date: 2007-03-24
forum: Desktop Effects &amp; Customization
---

### Post by thathatman on 2007-03-24
This is a multi-faceted question, so bear with me.

   My goal is to have the option to switch between a good open-source composited session with a non-composited session with proprietary drivers. The reason for this being that most of the time I would just like a nice-looking desktop, however, in the rare occasion that life allows it, to be able to play some 3D games. (The open-source drivers aren't quick enough with my aging setup to play games well.) This plan is based on the following thoughts:

1. I'm under the impression that, in most instances, for ATI users, the radeon drivers + AIGLX for composite support is a better idea (easier, nicer, stabler, less resources-intensive, et al) than fglrx + XGL. Is this actually the case? Has anyone compared both setups?

2. Assuming that that is true, would it be plausible to have a script to switch from radeon drivers to fglrx and automate the process for me? It might look something like this:
   a. swap out xorg.conf
   b. modprobe (if needed?)
   c. restart X
   d. have different sessions set up

This is by no means an urgent plea, just another step in the process of customizing my desktop. Let me know what you folks think!

---

### Post by russellc on 2007-03-24
You could create a simple bash script:

#!/bin/bash
cp /path/to/replacement/xorg.conf /etc/X11/xorg.conf
gksudo /etc/init.d/gdm reload

For different sessions, you would be logging in and selecting the other session..

---

### Post by murlosad on 2007-03-24
This is a good idea, I just started using an ati card and would like to be able to do something like this also. 

It would have to close out of your X session and launch a new one, so here's a thought... back in the day you could launch fullscreen games without a wm.  I can't remember the command and it was for XFree86.

If that's still possible why not a script to kill X, activate the fglrx drivers and a replace xorg.conf file and launch your game without having to even open up a wm at all.  And then on exit, have it reverse the changes and launch gnome or whatever again.

---

