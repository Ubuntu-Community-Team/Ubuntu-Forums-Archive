---
title: "eSATA not working on Dell Zino HD"
date: 2010-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mattlach on 2010-09-06
Hey all!

I already posted about this in the hardware thread, but on second thought it probably belongs here instead.

I recently picked up a Dell Zino HD to serve as my NAS with storage attached via eSATA. I have it running Ubuntu Server Edition 10.04.

My eSATA storage array (a Drobo S) is not useable after boot.

Here are what I think are the relevant portions of dmesg

```

dmesg| grep ata3


[    0.956381] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    1.880037] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.880430] ata3.15: Port Multiplier 1.1, 0x1a62:0x0003 r23, 14 ports, feat 0x0/0x0
[    1.880434] ata3.15: Asynchronous notification not supported, hotplug won't
[    1.881194] ata3.00: hard resetting link
[    2.410350] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    2.410399] ata3.01: hard resetting link
[    2.760497] ata3.01: SATA link down (SStatus 0 SControl 320)
[    2.760581] ata3.02: hard resetting link
[    3.110580] ata3.02: SATA link down (SStatus 0 SControl 320)
[    3.110677] ata3.03: hard resetting link
[    3.460581] ata3.03: SATA link down (SStatus 0 SControl 320)
[    3.460677] ata3.04: hard resetting link
[    3.810588] ata3.04: SATA link down (SStatus 0 SControl 320)
[    3.810685] ata3.05: hard resetting link
[    4.160584] ata3.05: SATA link down (SStatus 0 SControl 320)
[    4.160681] ata3.06: hard resetting link
[    4.510543] ata3.06: SATA link down (SStatus 0 SControl 320)
[    4.510631] ata3.07: hard resetting link
[    4.860586] ata3.07: SATA link down (SStatus 0 SControl 320)
[    4.860684] ata3.08: hard resetting link
[    5.210580] ata3.08: SATA link down (SStatus 0 SControl 320)
[    5.210676] ata3.09: hard resetting link
[    5.560584] ata3.09: SATA link down (SStatus 0 SControl 320)
[    5.560681] ata3.10: hard resetting link
[    5.910579] ata3.10: SATA link down (SStatus 0 SControl 320)
[    5.910675] ata3.11: hard resetting link
[    6.260585] ata3.11: SATA link down (SStatus 0 SControl 320)
[    6.260682] ata3.12: hard resetting link
[    6.610599] ata3.12: SATA link down (SStatus 0 SControl 320)
[    6.610689] ata3.13: hard resetting link
[    6.960590] ata3.13: SATA link down (SStatus 0 SControl 320)
[    6.960972] ata3.00: ATA-6: Drobo   3rd Gen DRDR3-A, v1.0.0, max UDMA/133
[    6.960976] ata3.00: 17179869184 sectors, multi 0: LBA48 
[    6.961352] ata3.00: configured for UDMA/133
[    6.961407] ata3: PMP SError.N set for some ports, repeating recovery
[    6.961465] ata3.00: hard resetting link
[    7.890351] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    7.891063] ata3.00: configured for UDMA/133
[    7.891114] ata3: PMP SError.N set for some ports, repeating recovery
[    7.891167] ata3.00: hard resetting link
[    8.820354] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    8.821063] ata3.00: configured for UDMA/133
[    8.821121] ata3.00: failed to recover link after 3 tries, disabling
[    8.821124] ata3.00: disabled
[    8.821128] ata3.00: PHY status changed but maxed out on retries, giving up
[    8.821131] ata3.00: Manully issue scan to resume this link
[    8.821137] ata3: EH complete

```

So it looks like it is trying to connect to the unit via eSATA 3 times and then gives up and disables the connection.  It says I can manually issue a scan to resume the link.

How do I do this?

Any other suggestions?

I explicitly asked Dell tech support before buying whether eSATA with port multiplier would work in Linux, and they assured me it would. (they sent me the chat log)  If I cant solve this I may try to get my money back and build my own server from scratch (which I should have done instead of being impressed by the small form factor and low price of the Zino HD)

Thanks,
Matt

---

### Post by Rachmadin on 2010-09-26
According to my experience, Zino HD eSata ports do not support port multiplier (or hot-swap). It is not documented at all - I have tried to find information about this, and then just made the assumption that if someone designed the Zino HD to have 2 eSata ports, they probably thought to include full eSata support. But this is not true. The Zino's eSata ports are just SATA ports with eSata connectors. This means no support fro Drobo, no support for Addonics storage tower, and do on.

eSata with port multiplier not only does not work in Linux, but does not work AT ALL with the Zino HD.

Who did tell you that the Zino was eSata port multiplier compatible?

---

### Post by mattlach on 2010-09-26
> **Rachmadin said:**
> 
Who did tell you that the Zino was eSata port multiplier compatible?

The Dell chat support on their webpage told me this when I was buying it...

Thanks for your input.

---

