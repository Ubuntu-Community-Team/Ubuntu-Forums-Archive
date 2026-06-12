---
title: "Wine + Sketchup + ATI : it works but...."
date: 2009-03-02
forum: General Help
---

### Post by Romu on 2009-03-02
Hi all,
As I need to work with Sketchup, I tried to make it work.

My environment is a Macbook Pro running Intrepid 64 bits and an ATI X1600 graphic chipset.

I tested Sketchup 6 French and Sketchup 7 English and tried the radeon, radeonhd and fglrx drivers. All registry tricks have been made.

First of all, it works only if the DRI is NOT activated, so forget fglrx, or if someone knows how to deactivate DRI on the fglrx driver, please let me know.

No DRI means, no Compiz effects, and as DRI deactivation is made in the xorg.conf, the Compiz-Switch workaround is not one anymore.

I gave up radeonhd driver, for sure it is the future of free ATI driver, but the radeon is much more advanced and has higher 3D performances, and it's pretty sensitive in Sketchup.

So the graphic configuration is pretty simple : radeon driver with DRI deactivated.

Regarding the Sketchup versions, both works, Sketchup 7 rendering is a bit better but has much more graphic artefacts. Sketchup 6 does not seem to display these graphics problems and so would probably be my choice. I will do some additionnal tests.

Hope this helps.

---

