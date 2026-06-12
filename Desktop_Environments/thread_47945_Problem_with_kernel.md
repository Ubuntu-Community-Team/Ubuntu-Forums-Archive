---
title: "Problem with kernel"
date: 2005-07-10
forum: Desktop Environments
---

### Post by paulfox on 2005-07-10
I've build a custom kernel based on the ubuntu sources. the kernel boots fine, and it's usable with all my hardware. the problem is that the init process isn't printed out on the screen during boot up. so it's impossible to see how the boot is progressing.
any ideas what i've left out of the config?

Cheers,
Paul

---

### Post by paulfox on 2005-07-11
any ideas folks?

---

### Post by FLeiXiuS on 2005-07-11
Whats your grub config look like?  Sounds to me like it may have framebuffering configured and not entered into the configurations correctly.  If not then there is a VESA module located in the configuration which is not compiled in the kernel.

---

