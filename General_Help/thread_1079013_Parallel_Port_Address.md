---
title: "Parallel Port Address"
date: 2009-02-23
forum: General Help
---

### Post by calvarymanagua on 2009-02-23
This may be a dumb question.  I am using EMC2 to control a CNC machine.  I recently bought a new computer to control the machine.  This computer did not have a parallel port on the mother board.  So I bought a PCI parallel port.  On the old machine, the old parallel port was at 0x378.  However, I have no idea how to find this for the PCI port on the new machine.  I have tried lspci -v, but do not really know which numbers I am looking for.  This is the output for the parallel port:

04:06.0 Communication controller: NetMos Technology PCI 1 port parallel adapter (rev 01)
	Subsystem: LSI Logic / Symbios Logic Unknown device 0010
	Flags: medium devsel, IRQ 4
	I/O ports at d050 [size=8]
	I/O ports at d040 [size=8]
	I/O ports at d030 [size=8]
	I/O ports at d020 [size=8]
	I/O ports at d010 [size=8]
	I/O ports at d000 [size=16]

Thanks

---

### Post by iaculallad on 2009-02-23
Try to list the available ports available by:

```
ls /dev/lp*
```

---

### Post by calvarymanagua on 2009-02-24
ls /dev/lp*
gives the following result:

ls: cannot access /dev/lp*: No such file or directory

I also tried: lsmod | grep parport

Which gives this result:
parport                33224  2 ppdev,lp

I have also read that I should look at the file /proc/ioports
Which has this:
0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : 0000:00:1f.1
  0170-0177 : libata
01f0-01f7 : 0000:00:1f.1
  01f0-01f7 : libata
0376-0376 : 0000:00:1f.1
  0376-0376 : libata
03c0-03df : vga+
03f6-03f6 : 0000:00:1f.1
  03f6-03f6 : libata
0400-047f : 0000:00:1f.0
  0460-047f : iTCO_wdt
0500-053f : 0000:00:1f.0
0cf8-0cff : PCI conf1
d000-dfff : PCI Bus #04
  d000-d00f : 0000:04:06.0
  d010-d017 : 0000:04:06.0
  d020-d027 : 0000:04:06.0
  d030-d037 : 0000:04:06.0
  d040-d047 : 0000:04:06.0
  d050-d057 : 0000:04:06.0
e000-efff : PCI Bus #03
  e000-e0ff : 0000:03:00.0
    e000-e0ff : r8169
f000-f01f : 0000:00:1f.3
f020-f03f : 0000:00:1d.3
  f020-f03f : uhci_hcd
f040-f05f : 0000:00:1d.2
  f040-f05f : uhci_hcd
f060-f07f : 0000:00:1d.1
  f060-f07f : uhci_hcd
f080-f09f : 0000:00:1d.0
  f080-f09f : uhci_hcd
f0a0-f0af : 0000:00:1f.2
  f0a0-f0af : libata
f0b0-f0b3 : 0000:00:1f.2
  f0b0-f0b3 : libata
f0c0-f0c7 : 0000:00:1f.2
  f0c0-f0c7 : libata
f0d0-f0d3 : 0000:00:1f.2
  f0d0-f0d3 : libata
f0e0-f0e7 : 0000:00:1f.2
  f0e0-f0e7 : libata
f0f0-f0ff : 0000:00:1f.1
  f0f0-f0ff : libata
f140-f147 : 0000:00:02.0

Which I really do not know how to interpret.

---

### Post by calvarymanagua on 2009-02-24
I guess I was making it too complicated.  I used the address:
0xd050 and everything is working.

---

