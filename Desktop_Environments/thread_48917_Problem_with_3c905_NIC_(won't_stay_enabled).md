---
title: "Problem with 3c905 NIC (won't stay enabled)"
date: 2005-07-14
forum: Desktop Environments
---

### Post by graza on 2005-07-14
Hi
I'm a new kubuntu user - everything works fine on my PIII machine except the network card.
I disabled the onboard motherboard NIC in BIOS and am using a PCI 3com 3c905 card (to take advantage of its mac address which is already registered here at work).
the card is displayed using lspci, and is working (ie lights on it are workin)

However under network settings from the control cetre it says eth0 is disabled, when I go into admin mode and enable it- for a few seconds it says its ok, then it spontaneously becomes disabled.

I think I can ping localhost OK from a shell, it goes off and gives a time of 0.1ms

IFconfig:
link encap:local loopback
net addr: 127.0.0.1 mask 255.0.0.0
up loopback runninh mtu 16436 metric 1
RX packets:16 errors:0 dropped:0 

etc etc

So, I take this to mean that the card is running, but there is still a problem somewhere.

One problem I still need to sort out is getting it to work with the LAN here, as its primarily setup for windoze machines by the administrators - on installation it reports that it cannot get a DCHP address (due to network settings here? poss the mac address has been switched off by the network admin)
However! surely this shouldn't affect the card - shouldn't it still be enabled even if the machine was not connected to a LAN?

All help gratefully received, I have a reasonable bit of experience with windows but would like to go linux if possible! \\:D/ 

Graza

---

