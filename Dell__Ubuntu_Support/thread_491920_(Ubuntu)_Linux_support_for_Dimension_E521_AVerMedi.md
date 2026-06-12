---
title: "(Ubuntu) Linux support for Dimension E521 AVerMedia M779 DVBt Hybrid TV Tuner"
date: 2007-07-04
forum: Dell  Ubuntu Support
---

### Post by sj3fk3 on 2007-07-04
I've also posted a question about Dell support for the M779 under (Linux) Ubuntu on the Dell support forum and are awaiting a response. The dutch Dell support has no clue and (therefor) does not want to support Ubuntu at all.

Let's start wirk lspci -vv output:
01:00.0 Multimedia video controller: Micronas Semiconductor Holding AG Unknown device 0720
Subsystem: Avermedia Technologies Inc Unknown device 032e
Flags: bus master, fast devsel, latency 0, IRQ 5
Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
Memory at fdee0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: [40] Power Management version 2
Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [58] Express Endpoint IRQ 0
Capabilities: [100] Device Serial Number 00-11-3c-20-07-00-00-00
Capabilities: [400] Virtual Channel

Now the questions:
Has anybody gotten the M779 working under Linux? I read somewhere that the card should be the same as the AVerMedia A16D but I seriously doubt this unless Dell is shipping M779 type card with different chipsets, because my lspci output does not mention a Philips chipset.

Secondly does anybody know exactly what chipset is used in the M779 and if it's compatible with anything already supported by video4linux?

Now I still need to boot my Dell E521 to Windows Vista to watch TV, while I would much rather just stick with the Ubuntu install thats working just fine apart from the tuner card.

---

