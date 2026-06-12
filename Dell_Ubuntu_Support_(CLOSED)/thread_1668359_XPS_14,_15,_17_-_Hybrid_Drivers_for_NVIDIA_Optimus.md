---
title: "XPS 14, 15, 17 - Hybrid Drivers for NVIDIA Optimus Updates"
date: 2011-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by krunalpatel on 2011-01-16
Just a thread i'm starting to let people know that currently there are drivers being worked on. For the new guys, when you install the nvidia drivers after new installation, your X will not start after reboot. Just sit tight and wait till a solution is released.



P.S.  If any of you are developers out there that are working on these drivers, and have some updates, please chime in. If you need any of us to be testers, let us know. Thanks

---

### Post by haecceity on 2011-01-17
Thanks for the update **krunalpatel** -- like many, I eagerly await some kind of work-around to the Optimus / hybrid issue. (New Dell XPS 17 owner here.) I'm a C/C++ developer so if there's any way I can help I might be able to spare some time.

I *thought* that after I did a fresh install of Ubuntu, compiz was working (transparent windows etc.?) but after accepting its evil offer to upgrade the NVIDIA drivers, compiz stopped working.  I initially got the terminal prompt after rebooting, but after deleting xorg.conf and rebooting again X launched successfully. Now I'm not sure which card it's using, nor how to tell. lsmod | grep nvidia shows nothing, so I guess that means it's using the Intel i915 driver?! Can the Intel onboard card even do flashy Compiz stuff?

I'm having the same issue with the brightness keys as others.  I tried the method you posted (thanks!) and it worked, but the price was that my touchpad and wireless ceased working -- perhaps because they didn't like the unexpected kernel version?

I also had the "suspend" issue that others have seen; it did indeed turn out to be the USB3 ports.  I fixed this issue by adding a script to remove xhci_hcd on suspend and reload it on waking.

By the way, what's the right way to know, erm, which version of Ubuntu I'm running?! /etc/issue says 10.10, but System | About Ubuntu says 11.04.  Huh?!

---

