---
title: "DMs/Xorg Crashes in Kernel 2.6.20.6"
date: 2009-01-20
forum: Desktop Environments
---

### Post by bgt421 on 2009-01-20
Hi all,

I'm seeking advice in troubleshooting an install of an older kernel that I cannot get the graphics working on. On my machine I have a flawless stock Ubuntu Kernel 2.6.27.9 from Intrepid, a flawless custom compiled kernel(same version), but I need a working version of the 2.6.20.6 Linux Kernel for a continuation of a kernel dev project by my major prof.

The problem I'm having is that I have a Radeon X300 video card, and under the older kernel with the open source driver Xorg would not run; all that displayed after the Ubuntu usplash was the monitor's "No signal" message. I went back in and reconfigured the kernel to have all the radeon drivers(as well as some framebuffers,etc) statically compiled. This had no effect. Finally, I installed the proprietary drivers (fglrx) for the card, and this bought me gdm (which appears to work flawlessly), and about two seconds of GNOME loading, after which the system is completely unresponsive. ALT-CTRL-BKSPC does nothing, and neither does attempting to switch to a virtual terminal. It seizes after the welcome music plays, and about half-way through loading the panels. I installed XFCE, and the same thing happens in that WM. The fail safe GNOME option also crashes in a similar manner. The only session that works is the X terminal option. When gdm loads, I can switch to a virtual terminal, but all I see are fast moving lines, as if VSYNC and HSYNC are wrong.

What is so puzzling about all this is that it is running the same distribution on the same machine. Specifically, the Xorg and xorg.conf, should be the same! What could be wrong?

I'll be happy to provide the .config s, or anything else that nay be useful.

Thanks!

---

