---
title: "BT878 Flyvideo TVCard No Sound One Channel"
date: 2006-01-21
forum: Desktop Environments
---

### Post by desperate_cry on 2006-01-21
Hi,

```

[4294696.552000] Linux video capture interface: v1.00
[4294696.603000] bttv: driver version 0.9.15 loaded
[4294696.603000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294696.607000] bttv: Bt8xx card found (0).
[4294696.607000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294696.607000] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 16, latency: 32, mmio: 0xe8000000
[4294696.607000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[4294696.607000] bttv0: gpio: en=00000000, out=00000000 in=00f4ff00 [init]
[4294696.628000] tveeprom(bttv internal): Huh, no eeprom present (err=-121)?
[4294696.628000] bttv0: using tuner=-1
[4294696.628000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294696.630000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294696.632000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294696.635000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294696.654000] bttv0: registered device video0
[4294696.669000] bttv0: registered device vbi0
[4294696.776000] bt878: AUDIO driver version 0.0.0 loaded
[4294696.781000] bt878: Bt878 AUDIO function found (0).
[4294696.781000] ACPI: PCI Interrupt 0000:00:08.1[A] -> GSI 16 (level, low) -> IRQ 16
[4294696.781000] bt878(0): Bt878 (rev 17) at 00:08.1, irq: 16, latency: 32, memory: 0xe8001000
[4294697.082000] irda_init()
[4294697.082000] NET: Registered protocol family 23
[4294697.429000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[4294697.429000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[4294697.429000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 6
[4294697.429000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294697.939000] codec_read: codec 0 is not valid [0xfe0000]
[4294697.945000] codec_read: codec 0 is not valid [0xfe0000]
[4294697.951000] codec_read: codec 0 is not valid [0xfe0000]
[4294697.957000] codec_read: codec 0 is not valid [0xfe0000]

```

as you see above i have a TV Flyvideo TV Card with BT878 Chipset. I tried TVTive xavtv KDEtv vs... and lastly i can watch one channel (last channel i opened on Windows), with no sound...

Any ideas? Suggestions?
(After a long walk, a working TvCard is the last step for an perfect desktop!)

Thanks!

---

