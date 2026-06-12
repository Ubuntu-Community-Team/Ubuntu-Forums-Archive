---
title: "window drag weirdness"
date: 2012-11-05
forum: Desktop Environments
---

### Post by mugenbb6 on 2012-11-05
I'm running 12.04, and whenever I drag a window around, the mouse pointer disconnects from the window.  If I continue moving the mouse, the window will still follow.  This happens on all my installations, so it's not an isolated incident.

---

### Post by 28c64 on 2012-11-05
That sounds like the same thing that happens to me before I install the Nvidia drivers.

Can you tell us which video drivers you are using and post the output of:

```

lspci -v

```

---

### Post by mugenbb6 on 2012-11-06
I'm running a ati 2600xt with amd's drivers.  I'll run lspci when I get home and post the output.

---

### Post by mugenbb6 on 2012-11-08
Here's the output:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV630 [Radeon HD 2600XT] (prog-if 00 [VGA controller])
    Subsystem: VISIONTEK Device 3370
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7d20000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at e000 [size=256]
    Expansion ROM at f7d00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV630 audio device [Radeon HD 2600 Series]
    Subsystem: VISIONTEK Device aa08
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f7d30000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

---

