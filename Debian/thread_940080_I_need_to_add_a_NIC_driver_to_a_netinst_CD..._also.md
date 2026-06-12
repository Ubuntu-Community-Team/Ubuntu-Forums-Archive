---
title: "I need to add a NIC driver to a netinst CD... also help me find the driver"
date: 2008-10-06
forum: Debian
---

### Post by MaxIBoy on 2008-10-06
I got this old computer (NEC ready-series 9935) for use as a server, and the netinst CD doesn't detect the ethernet card. It's a D-link DE220p (found out by opening the case, as the card didn't ship with the machine.) I *could* just go ahead and install a minimal system, but then I *still* wouldn't have the ethernet drivers, and I wouldn't be able to use it as a server.


The only drivers I can find for this are either for Windows or SCO Openserver 5. Supposedly it's usable with the "ne2000" driver, but once again, I can't find the drivers.

Where could I get the drivers, and how could I add it to the netinst ISO?

---

### Post by basenvironment on 2008-10-06
that is a VERY OLD nic, I would simply get a newer one....

---

### Post by MaxIBoy on 2008-10-06
I'd like to avoid investing money in this (got the computer for free.) However, if there's a "tried and true" NIC model I could get used and on the cheap, I'd be willing to go for it.

I suppose I'm lucky the motherboard doesn't have ISA slots.

---

### Post by basenvironment on 2008-10-06
Are you sure it doesnt have ISA slots? I thought the DE220p was an ISA card.

If you want, PM me to discuss cheap network cards.

---

### Post by MaxIBoy on 2008-10-06
It says "PCI" on the motherboard...

---

### Post by basenvironment on 2008-10-06
what color is the slot the card is plugged into? pci slots were usually white-ish and ISA was black-ish

How do you know it isnt detected? Are you getting any errors?

A good pci NIC shouldn't run more than 8bucks or so.

---

### Post by MaxIBoy on 2008-10-06
I found a $6 model (with $7 shipping, d'oh.)

I just checked, the NIC is indeed on an ISA slot (bigger than PCI, right?) but there are two available PCI slots as well. There's also an AGP, surprisingly. With a Voodoo 3dfx GPU in it!

---

### Post by basenvironment on 2008-10-07
> **MaxIBoy said:**
> I found a $6 model (with $7 shipping, d'oh.)

I would think you could find one for less. Maybe a used comptuer shop in your area.

I haven't used these in while but the network cards I always used are:
1)compaq branded card with intel chipset with a part numbers of NC3121 (make sure it has the big square intel chip on it)
2)3com 3c905c or 3c905b
3)Dlink DFE-530 REV D2

> 
I just checked, the NIC is indeed on an ISA slot (bigger than PCI, right?) but there are two available PCI slots as well. 
lucky there are pci slots!

> **MaxIBoy said:**
> There's also an AGP, surprisingly. With a Voodoo 3dfx GPU in it!
I wonder how much memory it has? Probably not enough to do anything except 640x480 or something. Probably wont matter for a server though.

---

### Post by MaxIBoy on 2008-10-07
Well, this *was* a media center PC in its time. 128 MB RAM, Pentium II, 9.5 GB hard drive, AGP Voodoo 3dfx. A puppylinux CD actually got 1024 by 768 out of it, if memory serves.

---

