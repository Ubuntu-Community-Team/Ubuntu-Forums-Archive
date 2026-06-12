---
title: "PCI Card"
date: 2009-02-07
forum: General Help
---

### Post by esullivan on 2009-02-07
How do I know if Ubuntu sees and has drivers for a PCI card?

---

### Post by issih on 2009-02-07
Well, if the hardware is seen I'm pretty sure it will show up in the output of the terminal command:

```
lspci
```

As for whether there will be drivers, that will depend on what it is :) if the kernel already has the drivers built in (happens more often than you'd think) the card will just magically work. If not you'll have some googling to do

Hope that helps

---

### Post by esullivan on 2009-02-07
> **issih said:**
> Well, if the hardware is seen I'm pretty sure it will show up in the output of the terminal command:

```
lspci
```

As for whether there will be drivers, that will depend on what it is :) if the kernel already has the drivers built in (happens more often than you'd think) the card will just magically work. If not you'll have some googling to do

Hope that helps

I tried that and did some looking around and found this
```

05:04.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0c)
	Subsystem: Lumanate, Inc. Device 001b
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at fc500000 (32-bit, non-prefetchable) [size=8K]
	Memory at fc503000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>

```

Why does it say access denied?

---

### Post by issih on 2009-02-08
No idea really...probably means there isn't a driver for it installed.

---

### Post by esullivan on 2009-02-09
> **issih said:**
> No idea really...probably means there isn't a driver for it installed.

I looked around a little and couldn't find anything.  I might have to just go buy a supported card.

---

