---
title: "Nvidia overclocking- coolbits doesn't work"
date: 2005-12-01
forum: Gaming &amp; Leisure
---

### Post by chimera on 2005-12-01
I added the "Option "Coolbits" "1"" line to the device section of the /etc/X11/xorg.conf , and the clock settings section in the nvidia-settings isn't showing up. What did I do wrong?

---

### Post by AndersAA on 2005-12-01
are you using a driver that supports it?  Keep in mind that current breezy does not have the latest driver.

Also, it doesn't seem to work on dual monitors, but you can use nvclock.

---

### Post by chimera on 2005-12-01
I don't know about the driver, I just downloaded and installed it with synaptic(by the HOWTO on ubuntuguide)

And I only have one monitor

---

### Post by AndersAA on 2005-12-01
well I cant remember which version added coolbits, but nvclock should work fine in either case.

---

### Post by chimera on 2005-12-01
Nvclock doesn't support my card (Leadtek Geforce A6600GT AGP)

---

### Post by AndersAA on 2005-12-01
ah, well, then you'll most likely have to install the latest nvidia driver.  Note that if your on amd64 that can be a real pain (because of 32bit libraries).  I think there's a howto either in the howto's forum or in the wiki for updating to the latest nvidia driver.

---

### Post by chimera on 2005-12-01
just checked, the one I have installed is 7667.

---

### Post by Yagisan on 2005-12-01
[QUOTE=chimera]Nvclock doesn't support my card (Leadtek Geforce A6600GT AGP)[/QUOTE]I built an nvclock backport from debian sid. You can find it, by clicking the link in my sig and adding the repo listed on the doomsday page. Please note that a) That is on my ADSL link so it is slow, b) may not always be up, and c) is completey unsupported and you use at your own risk.

That said, it works fine with my 6800LE with the breezy nvidia drivers.

---

### Post by chimera on 2005-12-01
Thanks a lot,it's detected now. Now I just have to wait for the new case and water cooling I ordered and I can get started with overclocking :)

---

