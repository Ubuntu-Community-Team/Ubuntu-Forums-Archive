---
title: "boot problem (possibly related to KDE install)"
date: 2008-12-07
forum: General Help
---

### Post by cclofton on 2008-12-07
hello, on booting I get the following error repeated for a minute or so:

```
[  376.694433] vc032x: probe of 5-7:1.0 failed with error -22
[  376.968248] usb 5-7: new high speed USB device using ehci_hcd and address 46
[  377.127396] usb 5-7: configuration #1 chosen from 1 choice
[  377.128479] gspca: probing 046d:0896
[  377.336537] vc032x: check sensor header 44
[  377.337335] usb 5-7: USB disconnect, address 46
[  377.337363] vc032x: I2c Bus Busy Wait 0
[  377.337372] vc032x: I2c Bus Busy Wait 0
[  377.337380] vc032x: I2c Bus Busy Wait 0
[  377.337388] vc032x: I2c Bus Busy Wait 0
[  377.337396] vc032x: I2c Bus Busy Wait 0
[  377.337403] vc032x: I2c Bus Busy Wait 0
[  377.337407] vc032x: Unknown sensor...
[  377.337428] vc032x: probe of 5-7:1.0 failed with error -22
[  377.616059] usb 5-7: new high speed USB device using ehci_hcd and address 47
```

Eventually it gives up and loads gnome, but tells me my .dmrc file permissions need to be changed to 644 (I changed them, it didn't make a difference).

I tried booting up a previous kernel and got the same errors, so the only thing I can think is causing this is a recent install of the KDE 4 desktop. Certainly it's easy to install, but removing it is not quite so simple, and I'm pretty sure something's got messed up. I've removed everything "KDE" in synaptic and reinstalled ubuntu destop bits, but to no avail. I could try blacklisting that usb device that's causing the problem, but there was no problem before so I don't see why I should.

And yes, I know KDE shouldn't mess up anything on this level, but I've not done anything else to my computer that could have caused it........actually, I just remembered I spilled my dinner all over it the other night, (never balance food near a laptop) but nothing popped or fizzed, so I presumed it was ok after a good clean up. When will they invent computers for clumsy people?

Anyway, help would be appreciated to save me having to do a complete reinstall

Thanks

cclofton

PS - to any other ubuntu novices out there thinking of installing KDE 4 because it looks shiny....think twice.

---

### Post by cclofton on 2008-12-08
anyone?

---

