---
title: "parallel kde4 sessions + compositing/opengl = no go?"
date: 2009-12-06
forum: Desktop Environments
---

### Post by CHaoSlayeR on 2009-12-06
Hi *,

I've recently started to utilize the "switch session" options and found out that the second+ sessions are not able to use hardware acceleration at all and the desktop system settings say, that compositing is "temporarily disabled". And any OpenGL app falls back to software mode (if it is able to, otherwise crashes or silently dies).

Additionally the borders/buttons/title-bar of windows are drawn very very slow and so is moving windows around and so on. This renders the multiple session feature almost useless if you know that you have a quad-core and a fast graphics card.

Why is that?
Does it have to be so?
Would using KMS make a difference here?

Hardware:
- Gigabyte GA-MA785GM-US2H motherboard
- AMD Athlon(tm) II X4 620 Quad-Core
- 4GB RAM
- ATI Radeon X1950XTX PEG (2x Dual-Link DVI)
- 2560x1600x32 @ 60Hz (Dell 3007WFP-HC)
- Microsoft Natural PS/2 keyboard
- Microsoft 5-button USB cable mouse

Software:
- Kubuntu 9.10 karmic
- radeon driver from xorg-edgers PPA (stock karmic doesn't make a difference)
- 2.6.32-15 kernel (vanilla 2.6.32 doesn't make a difference too)


The CPU usage of the system is not the problem - 90-95% idle.

The first session is dead fast including all compositing stuff.


Thanx for any hints/help here,

C]-[aoZ

---

