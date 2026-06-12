---
title: "d830 motherboard replaced; now nvidia drivers poweroff the system"
date: 2009-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by redchuck on 2009-03-09
I have a batch of 20ish D830s I support at work.  The motherboards have been dying, and have nearly all been replaced.  When the latest one was replaced, the 8.10 install on it no longer boots to X.  When the nvidia splash loads, the system powers off instantly without logging anything.  Reinstalling the nvidia drivers, or different versions of them, doesn't seem to help.

It boots fine without the nvidia drivers, and lshw is showing the hardware as identical to the old version, which worked.  The new hardware works in WindowsXP and works with generic drivers.  The only difference I can see seems to be that the BIOS has been upgraded from about 04 to 14.

Any idea what the problem is?  I'd really like to keep all these systems identical and not need to do unique fix on this, but Dell service says they don't support Ubuntu so it's not their problem.

[edit add] I've tried reinstalling the nvidia drivers with envy, but those also power off the system.  It's a Quadro NVS 140M video chipset.

---

### Post by redchuck on 2009-03-10
I ended up switching this machine to use the generic drivers, which work, but it would be lovely to know why it needed to be different from the rest.

---

