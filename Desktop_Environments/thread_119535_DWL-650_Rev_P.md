---
title: "DWL-650 Rev P"
date: 2006-01-19
forum: Desktop Environments
---

### Post by Pas3n7 on 2006-01-19
Hello all,

I need some help with my wireless card. The card is a D-link DWL-650 rev p. So it is the Prism 3 chipset.

The card is not being recognized with lshw, so I added the entry:

card "dwl-660 rev p. w/ Prism 3"
	manfid 0x000b, 0x7110
	function: 6 (network
	bind "ath_pci"

to /etc/pcmcia/config.opts (got the info from "sudo cardctl ident") and rebooted, but it still isn't recognized. The WirelessTroubleshootingGuide kinda stops off at this point so I am unsure where to go from here.

Any help would be quite welcome.

EDIT: The card is now recognized, but I can't figure out how to get a driver attached to it, lshw puts out:

*-network
     description: DWL-650 Wireless PC Card RevP
     product: ISL37101P-10
     vendor: D-Link
     physical id: 0
     version: A3
     slot: Socket 0

---

### Post by zjcim on 2006-08-05
i get the same card like you 
i am long for someone to fix it.

---

### Post by jcano88184 on 2006-08-29
I have the same card, lshw reports the same information, cardctl ident says it is the same Dlink dwl-650 rev. P... but i can't find the way ubuntu recognizes my card.
I have tried with ndiswrapper, nothing.

Is there any clue?

Thanks.

---

