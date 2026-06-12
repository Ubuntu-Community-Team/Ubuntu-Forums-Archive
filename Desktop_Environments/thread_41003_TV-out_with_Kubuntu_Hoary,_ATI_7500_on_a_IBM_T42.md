---
title: "TV-out with Kubuntu Hoary, ATI 7500 on a IBM T42"
date: 2005-06-11
forum: Desktop Environments
---

### Post by AndreasMeier on 2005-06-11
Hi all,

I'm running Kubuntu Hoary on my Thinkpad T42.
There is a ATI7500 running with the MESA-Drivers, no ati-drivers avail, but MESA can also provide 3D, no problem at all.

But now I'm trying to configure my TV-out and have read a couple of howtos, but all of them where for the ati-driver.

Can anyone give me some light and tell me, if I can configure TV-out with MESA and without the ati-drivers ?
Do I need additional programs (on my desktop I have the ati control-tool running) ?

Or can you provide me a good howto or parts of your running xorg.conf ?

Thanks in advance,
kind regards,
Andreas

---

### Post by emperor on 2005-06-11
This may be your only solution with the 7500. Howver their support for xorg is lagging and may require compiling from cvs. There is a binary for xfree86 4,3 and older xorg releases, so Warty or another distro would be easier.

[http://gatos.sourceforge.net/]("http://gatos.sourceforge.net/")

---

### Post by rawler on 2005-09-07
Actually, I'm a bit interested in the same thing. Running Ubuntu on a TP42, on the radeon driver with DRI enabled, and have spent around 8 solid hours on following various advices for getting tv-out from the 7500-card, without any success whatsoever. Gatos is the only thing I have not tried yet, but it seems a bit unsupported ATM?

---

### Post by emperor on 2005-09-07
Gatos is in the process of rolling the code into xorg. Next xorg release is suppose to include there binaries.

The Gatos mailing list is still active. I would suggest you subscribe and ask your questions there; as they are the ones that know the TRUE status.

---

