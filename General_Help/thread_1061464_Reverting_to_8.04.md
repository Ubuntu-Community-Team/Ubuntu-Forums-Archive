---
title: "Reverting to 8.04"
date: 2009-02-05
forum: General Help
---

### Post by zmzach on 2009-02-05
As some of you may know 8.10 has a bug which causes the entire system to randomely freeze up without hope of rescue with ctrl+alt+backspace or ctrl+f1. A hard reset is required. This has been going on for about 2 weeks now and nobody has any fixes for this problem, so I'm going back to 8.04 cuz I just can't deal with this.

Is there an easy way of doing this or do I have to completely reinstall?

Also I wanted to make sure that this is foresure going to fix my problem because this bug arose right after an update (my computer was working perfectly). I'm pretty sure that 8.04 still receives updates, so I just wanted to make sure that 8.04 isn't having this problem as well.

thanks

---

### Post by spiderbatdad on 2009-02-05
8.04 is an LTS (long term support) release and will continue to receive updates after 8.10 has reached it's end of support. Unfortunately reinstallation is required to revert. Most users do not experience the phenomenon you are talking about. Perhaps there are boot options that need to be incorporated into your kernel for Ubuntu to boot properly on your machine's hardware. This is not difficult to do. There is a basic guide here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you need more help, please ask more questions. Reading through the output of ```
dmesg
``` will sometimes make suggestions like "try using acpi=off." This is an indication to use "acpi=off" as a boot option.

---

### Post by abyssius on 2009-02-05
> **zmzach said:**
> As some of you may know 8.10 has a bug which causes the entire system to randomely freeze up without hope of rescue with ctrl+alt+backspace or ctrl+f1. A hard reset is required. This has been going on for about 2 weeks now and nobody has any fixes for this problem, so I'm going back to 8.04 cuz I just can't deal with this.

Is there an easy way of doing this or do I have to completely reinstall?

Also I wanted to make sure that this is foresure going to fix my problem because this bug arose right after an update (my computer was working perfectly). I'm pretty sure that 8.04 still receives updates, so I just wanted to make sure that 8.04 isn't having this problem as well.

thanks

Are you using an NVIDIA card? The symptom you describe has driven me crazy for months. No-one seems to acknowledge this, so I was unable to find a fix. This happened right after I did an update from 8.04.1 to 8.10. I re-installed 8.04.1 on a new partition, and it doesn't seem to have this problem. I've finally been able to use 8.10 without freezing by changing my graphics card to an old ATI I had in my parts bin. No more 3-D, but at least it doesn't lock up anymore. I had an NVIDIA FX-5200, when the problem surfaced. I've been investigating if this is an NVIDIA problem.

---

### Post by zmzach on 2009-02-06
Have a read here: [http://ubuntuforums.org/showthread.php?t=983459&highlight=8.10+randomly2+freezes](http://ubuntuforums.org/showthread.php?t=983459&highlight=8.10+randomly2+freezes)

This is the problem that I'm experiencing. I think it might have something to do with dual-core processors.

abyssius, I am using an ATI graphics card and having the problem. Does your cap locks light flash when it freezes up? this means a hardware incompatability. Mine doesn't flash

Thanks for the help, guess it's back to ol' trusty for me

---

### Post by jocko on 2009-02-06
> **zmzach said:**
> Have a read here: [http://ubuntuforums.org/showthread.php?t=983459&highlight=8.10+randomly2+freezes](http://ubuntuforums.org/showthread.php?t=983459&highlight=8.10+randomly2+freezes)

This is the problem that I'm experiencing. I think it might have something to do with dual-core processors.

abyssius, I am using an ATI graphics card and having the problem. Does your cap locks light flash when it freezes up? this means a hardware incompatability. Mine doesn't flash

Thanks for the help, guess it's back to ol' trusty for me
If the caps lock led is flashing, it indicates a kernel panic, i.e the kernel has found an error it cannot recover from safely, so it freezes up to prevent instability or data corruption. This can be caused by either software (kernel or drivers) or hardware errors, not only hardware incompatibility.

I had a problem in 8.10 (x86_64), where the keyboard and mouse buttons stopped working (but the mouse pointer could still be moved around), and the only way to get back was to do a hard reset (neither Ctrl+Alt+Backspace, Ctrl+Alt+F1 or Alt+SysRq+REISUB did anything).
In my experience this only happened when compiz was running with the 177.xx nvidia driver, and often when a new window was opened or directly after restarting compiz after a crash (which happened quite often).
After I installed the 180.27 driver from nvidias website I haven't seen any freezes, and compiz doesn't crash anymore.

---

