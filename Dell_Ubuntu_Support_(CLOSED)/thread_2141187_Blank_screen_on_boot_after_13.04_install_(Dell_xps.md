---
title: "Blank screen on boot after 13.04 install (Dell xps 13)"
date: 2013-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by toogooda on 2013-05-01
Hi,
I have installed 13,04 on my dell xps 13 laptop but find that most of the time I boot to a blank screen with nothing but mouse pointer (which you can still move around) strange thing is I have found that if I plug in an external monitor to suddenly works on both screens and I can unplug and use like normal (until it boots again).

Its like it thinks I have selected to use another screen that does not exist.

What I have tried:

Fn+F1 (Monitor select hot key)
Slowing down the boot some times fixes it IE lots of key strokes at startup

Was working on 12.10 but had dual boot then

Not sure what the exact VGA chip it has but lspci -v gave me this:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 052e
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 2000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

Have no issue with livecd/usb booting.

Any ideas?

Thanks in advance for any help

Cheers,

Andrew Toogood

---

### Post by toogooda on 2013-05-01
Interesting,

Just did my first lot of updates and noticed they were all related to boot and lightdm (the very things that seem to be having issues)

have done two restarts since with no issues, as it is intermittent I don't yet know if it is fixed.

Will post back tomorrow if no issues as it used to happen 9 times out of ten before.

Cheers,

AT

---

### Post by toogooda on 2013-05-02
I can confirm that the updates on 02/05/2013 fixed all the issues :)

---

