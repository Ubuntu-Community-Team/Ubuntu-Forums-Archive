---
title: "Pentium D, SMP-686, nVidia, X11 Hangs"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Giblet5 on 2006-09-03
I installed 6.0.6-1 (server) on a Pentium-D 920 box.

It worked great, but it's UniProcessor and 386 code. Boo. Hiss.

If I install the 686 linux-images, it boots up to the X11 welcome but the mouse and keyboard are frozen.

If I build a 686 SMP kernel and install it, I get the same thing.

Pentium-D 920
nVidia Gefore 6600
2GB DDR2

Any ideas? Is this a builtin-nvidia driver issue?
](*,)

---

### Post by Giblet5 on 2006-09-03
Update:
I reinstalled with Desktop. Again, works great, but is 386UP.

I installed the 686 image (same version - 2.6.15-23, I think) and rebooted in 'recovery mode'.

It boots to a # prompt but accepts no input, the system is 100% unresponsive via console or LAN. No disk activity.

Rather annoying...  Teh Googles yield nothing.

---

### Post by Giblet5 on 2006-09-03
Yet another update:

I have an identical problem to that reported in:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/9357](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/9357)

The status says fix released as of (I presume) 2.6.15-9, but I'm using 2.6.15-26 and the behavior is still there.

Maybe this is an MSI motherboard APIC issue? I don't claim to be an APIC guru - I can barely spell it - but when I disable APIC in BIOS, I can boot successfully in 686-UP mode.

I didn't test the "noapic" option on the kernel -- maybe that's all that was corrected.

Now what?

---

