---
title: "Desktop effects could not be enabled"
date: 2009-11-15
forum: Desktop Environments
---

### Post by 82urock on 2009-11-15
I recently installed ubuntu linux 9.4. whenever i select the option of moderate visual effect in appearance preference i get message "DESKTOP EFFECT COULD NOT BE ENABLE" I installed python opengl but same problem is persisit. what should i do?

---

### Post by fancypiper on 2009-11-15
What's your video card?  Have you installed the driver for it?

---

### Post by dirtlamb5 on 2009-11-15
I'm having the same issue as 82urock in karmic. I know my graphics card is capable of the desktop effects because it was working a couple days ago and it worked when I booted from the livecd, but I must've done something wrong and now I can't enable any visual effects.

Anyway, this this is what lspci -v says about my graphics card when I run it in the terminal:
```

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
    Subsystem: Dell Device 020d
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ff00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```I've seen others suggest "sudo dpkg-reconfigure xserver-xorg" and "sudo apt-get install --reinstall xserver-xorg" for this problem, but neither of them worked. When it was working before I don't remember having to install any drivers, so I don't think that's the issue.

---

### Post by dirtlamb5 on 2009-11-16
...bump. Anybody?

---

