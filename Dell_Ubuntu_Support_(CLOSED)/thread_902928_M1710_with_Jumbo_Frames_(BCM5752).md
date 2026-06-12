---
title: "M1710 with Jumbo Frames (BCM5752)"
date: 2008-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mike770780 on 2008-08-27
I have a Dell XPS M1710 with a build-in Broadcom NIC (BCM5752). I am trying to set the MTU for the interface to 9000 bytes in Ubuntu Linux. I know the card permits such a function because in Windows I can set the MTU to 9000 with proper functionality.


# ifconfig eth0 mtu 9000
SIOCSIFMTU: Invalid argument


I've been in touch with Dell and Broadcom tech support.

Dell tech support refers me to the manufacturer (broadcom).
Broadcom tech support doesn't answer my question. When I call their tech support and ask my question I am forwarded to a recording instructing me to call the distributor, in this case Dell.


below is the info from lspci -v for the card


09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Dell Unknown device 01ce
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ecff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Message Signalled Interrupts: 64bit+ Queue=0/3 Enable-
	Capabilities: [d0] Express Endpoint IRQ 0

Help!

---

