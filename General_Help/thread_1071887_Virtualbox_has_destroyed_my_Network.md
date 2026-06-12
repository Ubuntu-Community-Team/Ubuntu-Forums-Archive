---
title: "Virtualbox has destroyed my Network"
date: 2009-02-16
forum: General Help
---

### Post by dai_vernon on 2009-02-16
This has happened twice.

I have a perfectly running Ubuntu 8.10 installation and I attempt to install Virtualbox from through add/remove.  It installs fine but soon after, the system has a kernel panic (flashing leds and all).  I reboot to find my ENTIRE NETWORK ACCESS ABILITIES ARE GONE.  Plugging in an ethernet cable does not work, nor does wireless.  I uninstalled virtualbox and the source package, and they still did not work.  I recompiled and reinstalled my wireless driver kernel module, and this still did not work.  Rebooting and using an older kernel (2.6.27-9 instead of -11) works.

Clearly something in my kernel has been tampered with by Virtualbox.  What might it be and how might I fix it?

My previous fix was to nuke the entire install and reinstall.  I do not want to do this.

---

### Post by dai_vernon on 2009-02-16
So, like, in true ghost in the machine fashion, everything is better now for absolutely no reason.

All I did between then and now was boot the old kernel version.  I am now back in 2.6.27-11 and everything is fine...for no reason at all.

I guess the problem is solved, but I am curious to know what the hell happened...

---

