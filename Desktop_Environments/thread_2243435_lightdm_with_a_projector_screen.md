---
title: "lightdm with a projector screen"
date: 2014-09-08
forum: Desktop Environments
---

### Post by benlevitt on 2014-09-08
Long time ubuntu-user here.

I have an ubuntu server 14.4 machine all set up to use with my projector as the only screen.  When the projector is off, ubuntu doesn't detect any monitor plugged in.  But a long as the projector is turned on while lightdm is starting, it detects the projector as the monitor and all works great.  I'm okay with having to have the projector on when starting up.  It would be nice to fix, but not a dealbreaker.

My real problem is that once I turn off the projector overnight, and leave ubuntu running, the next morning when I turn the projector on, there's no signal.  If I ssh in and restart lightdm, then it happily restarts and shows the screen again.

I know that lightdm, X, and my running desktop programs are not being killed.  If I check ps, they're all still running.  I just can't see them.
I've disabled xscreensaver.
I set display blanking to Never in the lightdm settings.
I run these commands when my x session starts:
   xset -dpms s off
   xset s off
   xset s noblank

Any suggestions as to what might be blanking my screen?

Thanks very much!

Ben

---

