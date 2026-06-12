---
title: "Dell Inspiron (no PCMIA) - Wireless Help"
date: 2007-07-31
forum: Dell  Ubuntu Support
---

### Post by Renegade60 on 2007-07-31
Just acquired a new Dell Inspiron laptop with Ubuntu 7.04..

Was thinking of utilizing it as a mobile wireless network audit box, but just noticed that these new Dells only come with an ExpressCard slot and no older PCMIA slot..

So, I can't use my Orinoco Gold card with antenna they way I do on my other machines..

Anyone familiar with any Debian Linux friendly ExpressCard to PCMIA adapters?

Or are there any ExpressCard wireless A/B/G adapters that support Debian Linux and the use of an external antenna?

Or, and maybe this is my best solution, is there a USB wireless adapter that supports and external antenna and works with Ubuntu?

Thanks..

---

### Post by overdrank on 2007-08-01
> **Renegade60 said:**
> Just acquired a new Dell Inspiron laptop with Ubuntu 7.04..

Was thinking of utilizing it as a mobile wireless network audit box, but just noticed that these new Dells only come with an ExpressCard slot and no older PCMIA slot..

So, I can't use my Orinoco Gold card with antenna they way I do on my other machines..

Anyone familiar with any Debian Linux friendly ExpressCard to PCMIA adapters?

Or are there any ExpressCard wireless A/B/G adapters that support Debian Linux and the use of an external antenna?

Or, and maybe this is my best solution, is there a USB wireless adapter that supports and external antenna and works with Ubuntu?

Thanks..

HI if you have not found a answer to you issue this link may help
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Good luck and hope this helps. :)

---

### Post by ticklecricket on 2007-08-01
D-link DWLG122 has an atheros chipset and works like a charm.

---

### Post by Drizzt321 on 2007-08-05
About the Expresscard slot, there are a couple of things to note about it. It offers either a USB2.0 or 1xPCI-Express connection for a card. Cards come in either 34mm or 54mm form factors. There are no 'drivers' for the Expresscard slot itself. As long as the chipset which provides the USB/PCI-Express support is supported, it'll work. 

Now here's the caveat to all of that. If you have a card that works off of the PCI-Express bus, you may not be able to hotplug it. The problem is that PCI-Express hotplug driver (pciehp) needs a specific BIOS call to be available, and not all venders do (my Inspiron e1505/6400 doesn't :( ). Now you can also try the acpiphp drivers which works like XP does for PCI-E hotplug, but for me it unfortunately won't even load up, so I don't know how well it works. 

Read more at this whitepaper from MS on how XP vs Vista does PCI-E hotplug events. Its quite a good read.

[http://www.microsoft.com/whdc/system/bus/pci/BIOS_HotPlugPCIe.mspx](http://www.microsoft.com/whdc/system/bus/pci/BIOS_HotPlugPCIe.mspx)

--Aaron

---

