---
title: "Support for Serial port via Super IO chipset"
date: 2009-11-17
forum: Desktop Environments
---

### Post by shekharrana on 2009-11-17
Folks,
I installed Ubuntu 9.04 on my machine recently.
My machine config: Dell PC, based on Intel P4 2.8GHz processor. ..1GB RAM..
On my machine i have one Serial port, which doesnt seems working....I downloaded the kernel source using APT-GET, and found that Serial driver support is enabled.
so then i tracked the Serial port in hardware and found that Serial port is connected via a Super IO chipset.
so the topology on my machine is like:
Intel P4 <--> NorthBridge<--->SouthBridge<-->SuperIO<-->Serial Port

But i guess all Intel Based PC would be following the same topology..isnt it!!

any hints on how do i enable support for SuperIO UART ,,,,OR whether its supported at all or not.. woould be apprciated..


thanks

---

