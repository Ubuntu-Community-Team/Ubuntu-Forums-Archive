---
title: "Dell Dimension 8200 desktop w. GeForce 5200 won''t wake up"
date: 2012-09-28
forum: Desktop Environments
---

### Post by jgr007 on 2012-09-28
I've run Xubuntu reasonably well for years.  I was running 11.10 and a few weeks ago I after a patch update it started going to sleep and it will not wake up.  I believe this happened after a nvidia 173 patch update, but I'm not positive.  I've upgraded to 12.04 and still have the same problem.  In order to wake my desktop up I have to push the power button on and off between 3-6 times.

I believe it may be a problem with old GeForce FX5200 graphics card.

I've tried several several different thing (xset, mod x conf file, grub) and none of them seem to work.

Is there any way to just completely rip out all power management from Xubuntu?

---

### Post by Wim Sturkenboom on 2012-10-13
Have you tried nomodeset? Replace 'quite splash' with 'nomodeset'
Have you tried to boot to console instead of GUI? Repalce 'quiet splash' with 'text'.

If you don't know what I'm talking about (but I guess you do), let us know.

---

### Post by jgr007 on 2012-10-16
Thanks, Wim.

I tried nomodeset but still have the same problem.  I'm almost certain it happened with either a recent kernel or nvidia-173 update.  I have 3.2.0-32-generic kernel.  The problem started occurring prior to this kernel, but an upgrade to this one didn't solve it.

I can't really try the text option, because the problem doesn't occur until the machine has been on for a long time (and I don't know how long 'long' is).  If the machine stays on for a while...say all day...and then I turn it off the monitor will not wake and I have to start/restart with the button between 5 and 20 times to get it to wake up.  Starting in text doesn't work because I need to use the machine and I can't let it sit for several hours in text mode.  Because it sits so long before the problem occurs, it also makes it hard to figure out what is happening.

Incidentally, I also have my old CRT TV hooked up to the s-video output as a second monitor.  The CRT/s-video has no problem with display.  I can reboot/start the machine at any time and it works fine.  It's just the monitor on the VGA port that has a problem.


> **Wim Sturkenboom said:**
> Have you tried nomodeset? Replace 'quite splash' with 'nomodeset'
Have you tried to boot to console instead of GUI? Repalce 'quiet splash' with 'text'.

If you don't know what I'm talking about (but I guess you do), let us know.

---

