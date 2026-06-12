---
title: "Restricting X server display to only one head in multihead setup"
date: 2009-09-16
forum: Desktop Environments
---

### Post by cpdohert on 2009-09-16
I have a multihead setup based off of a laptop with dual video out and two monitors, a CRT VGA monitor and the built-in LCD.  Although I have multiple display outputs, I only want the X server to display on the external VGA monitor (I'm running something else that draws directly on the internal LCD screen, and X conflicts with it).

I've worked with X before and this used to be fairly simple, if a lot of xorg.conf trial and error. Under Ubuntu 9.04 so much is being done automagically in X that any time I think I've got it set up correctly, on reboot the system returns to a cloned display across two monitors.

Does anyone know of a decent Xorg reference that might explain how to restrict the X server to just the one monitor or the other?

---

