---
title: "Wifi stopped - but why?"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Sendervictorius on 2005-11-28
I had a working wireless connection (D-Link Airplus DWL-520+ Wireless PCI NIC, ndiswrapper) . I cleaned up some unused kernel packages and when I rebooted my wlan stopped working. Trouble is, I can't understand why, or which removed package was the vital one.

The story went like this:

I updated breezy with the latest linux kernel (2.6.12-10-k7) and headers.  By accident I also got the latest 386 kernel. So the grub menu was pretty full of old kernels. After checking that the new k7 kernel was working ok (wlan was ok too),  I removed all the old kernel and headers packages (using synaptic). When I re-booted  the wlan wouldn't connect. I know it was the package removal that did me in, because thats all I changed between boots.

Does anyone know what vital bit I removed - or what I should check to narrow down the problem?

---

