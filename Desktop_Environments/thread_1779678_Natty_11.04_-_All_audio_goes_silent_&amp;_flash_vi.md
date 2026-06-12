---
title: "Natty 11.04 - All audio goes silent &amp; flash videos play much too fast"
date: 2011-06-10
forum: Desktop Environments
---

### Post by Digital_Man on 2011-06-10
Today I encountered a bizarre problem which I've thankfully solved, but others may benefit from learning about my experience.

I was running a lot of CPU heavy software when all of a sudden Natty crashed. When I booted again, no audio was working on my machine other than the simple speaker test in System > Preferences > Sound Preferences.

Also very curious, any flash videos were playing back at lightning fast speed, like a Benny Hill segment.

I tried purging flash from the machine and reinstalling - the problem persisted.

In searching around, I found this site:
[http://www.shcherbyna.com/?p=946](http://www.shcherbyna.com/?p=946)

Once again under System > Preferences > Sound Preferences, there was both the internal audio on the mother board enabled, as well as a sound card associated with my ATI video card: RV710/730. The speaker test only worked on the internal audio and not the RV710/730. I just disabled the RV710/730 and all of a sudden, everything was working perfectly again: all audio played just as it should and flash videos were back to normal.

Clearly there was some conflict going on between my two audio cards and the solution was ridiculously simple. But why this problem chose to present itself now and not earlier (or even back on Maverick) is a mystery to me. I'm pretty sure that both audio cards had been enabled all along leading up to the problem.

Regardless, my system is working well again and that's all that matters.

---

### Post by moosee333 on 2011-09-22
Thanks sooo much!

---

### Post by maxniko on 2012-01-24
Thanks a lot, man! I had already pulled some hair out on this matter. I just disabled the Radeon X1200 HDMI output and everything came back to normal :D

By the way. I'm using 11.04 Natty but for some reason I can't access my info to update the field of the distro I'm using.

---

### Post by terry_n_brown on 2012-01-28
Thanks, fixed the problem immediately :-)

---

### Post by Kiril Papaz on 2012-06-05
Hi everyone!

I tried all steps but after typing: pavucontrol i see only one option under Configuration. See attachment.

Radeon X1200

I still have no sound. Any advice?

Thanks.

---

