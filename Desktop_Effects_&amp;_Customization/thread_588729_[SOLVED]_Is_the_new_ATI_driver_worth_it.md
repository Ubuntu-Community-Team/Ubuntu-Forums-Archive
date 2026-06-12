---
title: "[SOLVED] Is the new ATI driver worth it?"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by bobbob1016 on 2007-10-23
I have an x600 in this computer.  It runs ok with AIGLX and the open driver.  I am curious if it is worth it for me to upgrade to the new ATI driver.  Everyone says they get a lot of speed increases, but I don't know if that is from XGL to AIGLX or not.  Compiz works ok now, but if I do scale and I have a few windows open, it chugs, I just see the end result of the scale.

If is worth it, and anyone has the guide they used, I'd appreciate it.  Thanks.

---

### Post by grazzt on 2007-10-23
I just tried it on my X800 (R420), and not impressed at all.

Yes, compiz now "works", but so many other crucial things are screwed up.  Firefox scrolling is like its being run on a 386, and movie playback with XV and SDL are messed. :/

Luckily the opensource driver for me is good enough.

I would still recommend at least trying it though, maybe youre results will be better.

---

### Post by billybob123 on 2007-10-23
I had to fiddle with the location of fglrx.ko to get everything running - installer put it in /lib/modules/2.6.22-14-generic/misc/ but modprobe looked in /lib/modules/2,6,22-14-generic/volatile.  Copying fglrx.ko over worked if anyone else is having this issue.

That said, the performance on my X300 is much worse than using the radeon driver, which was very usable.  Only complaint with radeon is that firefox scrolling isn't so hot, but its even worse with fglrx 8.42.

---

### Post by bobbob1016 on 2007-10-23
I don't want to risk a working compiz, thanks for replying though.

---

