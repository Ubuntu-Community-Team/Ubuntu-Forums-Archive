---
title: "CPU usage 3% in top, but 50% in system monitor"
date: 2005-10-26
forum: Desktop Environments
---

### Post by OneSeventeen on 2005-10-26
I added the system monitor to my top pannel, and the bright blue lines stay down pretty low, but the dark blue ones in the background stay around 50% or more.

#top shows 3% CPU usage or less, depending on what I'm doing, but hovering over system monitor fluxuates between 47 and 56%.

My clock is also running at double speed.

I am passing no_timer_check to the kernel, which I was told should solve the clock/50% usage issue, but it isn't.

This is on a HP zv6000 laptop using an ATI Radeon Xpress 200M if that makes a difference.

I am using ati drivers with option "noaccel" and I have not specified the amount of video RAM available.  (should be 128MB)

---

