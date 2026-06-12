---
title: "Gnome and two monitors, problems."
date: 2010-03-01
forum: Desktop Environments
---

### Post by fackamato on 2010-03-01
Hi,

I'm using a Lenovo T400 laptop with an integrated Intel chipset, the module in use is i915. I've an external monitor connected to the VGA out, which at boot acts like it's cloned to the laptop screen. When I log into Gnome, it acts as an extension to my laptop, as I want it.

Problems:

* Volume change notifications (and possibly other notifications) appear on the external monitor, not the laptop monitor where I have all the Gnome stuff (panels etc).
* Using rdesktop, ctrl+alt+f (full screen) spans both monitors, which is wrong. Desired result: span the entire monitor that it's already active on, not both.
* I can't change the behaviour from cloned mode at boot on a kernel command line. Is this possible? I.e. i915.clone=0 or something.

Any help?

---

