---
title: "I Want my nVidia GeForce GTX 960 fanspeed to 100% ALWAYS"
date: 2016-07-04
forum: Gaming &amp; Leisure
---

### Post by psychoticusrex on 2016-07-04
My System: nVidia GeForce GTX 960 - PCIe/SSE2; in a Xubuntu 16.04 OS;  Linux 4.4.0-28; AMD FX 8350 (8-core); 16 GB ram; ASUS M5A97 R2.0 m/b, nVidia proprietary driver 367.27.

Previously under WinXP, Win10 and linux distro's under other cards and driver versions nvclock has worked (--fanspeed 100 (--force)) but under my current upgrade I can't get it to work.

I upgraded OS's and Cards and a lot else at same time so can't quite isolate the problem.

When I issue command:
```
sudo nvclock --fanspeed 100 --force
```
I get:
```
Error: Your card doesn't support fanspeed adjustments!
```

Also nvclock_gtk (latest package) doesn't add additional functionality as it just "crashes".

Is this a case of hardware jumping ahead of software or am i just a bad person (not well enough versed in linux lore to configure the system properly.).

I am not some wuss who quails at fan noise; rather I want the @#$@# thing cranked up to 11 all the time so my cards' longevity will be extended!

Please, if i just need to write up some C/ASM to trigger it directly i'm game but I need details i don't have resources to research.  A little help please.

---

### Post by Bucky Ball on 2016-07-04
You can't adjust the fanspeed through the NVidia configuration GUI that would be available in your apps if you have the NVidia driver installed from Additional Drivers or elsewhere?

---

### Post by psychoticusrex on 2016-07-05
The nVIDIA X Server Settings allow one to change the: PowerMizer Settings - Proferred Mode - (Auto, Adaptive, Prefer Maximum Performance).

Since these settings affect pseudo-over-clocking-on-rails I'm not really interested; the stock performance is more than fine, I just want the thing to hanging out in the COOL regime and not the BOIL WATER regime.

---

