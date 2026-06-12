---
title: "Suddenly screen size is wrong (Gutsy)"
date: 2007-10-18
forum: Desktop Environments
---

### Post by Bjoern on 2007-10-18
When I first installed Gutsy today, it detected the correct screen size (1920x1200). Now I just started my laptop again, and it doesn't detect the correct screen size anymore. The highest I can select is 1600x1200, although it shows the correct Monitor Model (Dell 2405FPW). 

I use the intel modesetting driver on a Latritude X1 laptop. 

Edit: I justsaw that there is a "Widescreen" checkbox if I click on the monitor details. Now I could select 1920x1200, but must log off before changes take effect (hopefully).

I hope it will work, and also, that the settings will be remembered...

---

### Post by DavidTangye on 2007-10-18
> **Bjoern said:**
> I hope it will work, and also, that the settings will be remembered...So did it :-).

---

### Post by Bjoern on 2007-10-19
It seems to work now that I also clicked "make this the default", but I don't trust it completely yet - Gutsy seems to be struggling and resizing after booting quite a lot, but so far it usually ended up with the right screen size.

I still have the other problem with windows resizing themselves. When I maximize them, they don't go fullscreen, but only to a part of the screen. Occasionally hey go to fullscreen and snap back to a part of the screen shortly after. Even the screensaver preview only shows up in the smaller part of the screen (not fullscreen).

So I suspect Gutsy is still confused about the screen resolution. I tried commenting out the "Virtual" line in the xorg.conf, but that didn't change anything.

---

