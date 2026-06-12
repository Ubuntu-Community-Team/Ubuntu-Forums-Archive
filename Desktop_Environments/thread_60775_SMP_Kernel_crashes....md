---
title: "SMP Kernel crashes..."
date: 2005-08-29
forum: Desktop Environments
---

### Post by hurenkam on 2005-08-29
Hi,


I'm running Kubuntu on a dual-athlon (Asus 266-D/AMD MP2600+) and dual video card system (Matrox G550AGP/Matrox G450PCI).
I have been using a Gentoo system with ruby patched kernel to get a dual-console setup, but recently switched to kubuntu because it has all the required patches for xorg in place to run dual console without kernel patches.

After installation, I focussed on getting X properly set-up, and that seems to work perfectly now, I have two X consoles using evdev for keyboard/mouse, and the -novtswitches and -singlecard options etc. So now I have a primary boot console on my primary G550 screen, an accelerated X server on my primary G450 screen, and a framebuffer X server on my secondary G450 screen. 
Seems the multiconsole X works really great :-)

But now, I tried to move to a SMP kernel, but have not been able to find one that works for me, any of the pre-built images (2.6.10 or 2.6.11) be it 386, 686, or k7, all seem to experience crashes (without any panic messages whatsoever) after about 5 to 30 minutes of use....
Even kernels built from scratch using my working gentoo config do not work.
Since there are no messages printed, I have no clue wether it's the kernel, X or something else which is causing it (could even be an unrelated driver).

Does anyone have any hints/tips I could try? So far I have only been able to get Ubunto to work with a non-smp kernel, which I find a terrible waste of CPU power :-(.

Does anyone else experience similar problems?


Warm regards,
Mark.

---

