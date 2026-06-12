---
title: "NVidia and Intel i810"
date: 2005-10-01
forum: Desktop Environments
---

### Post by weiln on 2005-10-01
I have two Dells, an Optiplex GX110, and a Dimension L733R.  Both have integrated video, and I have a NVidia TNT2 PCI card.  I can see the card in "lspci", is pci address is: 

0000:01:09.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

However, if I don't have the BIOS set to "Onboard" and have it set to either "PCI" or "Auto" depending on the BIOS, GDM never starts.  Ubuntu starts up normally, going through all the hotplug, network config, etc., but then all I get is a black screen once GDM is supposed to start.  The installation didn't have this problem, it ran off the NVidia PCI card, but I can't use the PCI card now.

How do I setup X to use the PCI NVidia card?

Thanks!

Nathan

---

