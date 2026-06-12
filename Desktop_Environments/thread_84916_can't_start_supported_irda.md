---
title: "can't start supported irda"
date: 2005-11-01
forum: Desktop Environments
---

### Post by mirons on 2005-11-01
Hi everybody! I'm trying to set up irda port in order to sync my palm, but while I manage quite easily to do it under knoppix (3.7, kernel 2.6.9), ubuntu seems disable by default this port. This is what kernel says

> 
[4294692.109000] irda_init()
[4294692.109000] NET: Registered protocol family 23
[4294694.910000] pnp: Device 00:06 disabled.
[4294694.910000]     ACPI-0508: *** Error: Method execution failed [\_SB_.PCI0.SBRG.UAR2._SRS] (Node dffead40), AE_AML_BUFFER_LIMIT


I thoght setpnp was the right tool to solve the problem, but it just tell me  /proc/bus/pnp is unavailable.
The modules to handle irda are there

> 
$ lsmod | grep ir
irtty_sir               8512  0
sir_dev                18444  1 irtty_sir
irda                  187612   2 irtty_sir,sir_dev
crc_ccitt               1984   1 irda


But the device isn't. (Absolutely no way to generate any sort of i/o on it, ttyS1 at I/O 0x2f8 (irq = 3), according to windows/kernel data)

---

