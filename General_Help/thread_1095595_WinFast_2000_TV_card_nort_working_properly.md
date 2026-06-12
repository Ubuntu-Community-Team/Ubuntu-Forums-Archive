---
title: "WinFast 2000 TV card nort working properly"
date: 2009-03-13
forum: General Help
---

### Post by bowens44 on 2009-03-13
I have a WinFast 2000 XP TV card that worked perfectly on Ubuntu 8.04 but is unusable on Ubuntu 8.10. 

The card is detected and I am able to scan the channels. The problem is that the video is very jerky. It constantly starts and stops. 

I followed this HOWTO but it didn't solve the problem.
[http://joeb454.ubuntuforums.org/showthread.php?p=6767109](http://joeb454.ubuntuforums.org/showthread.php?p=6767109)

[   13.522845] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[   13.522847] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]

The card was detected correctly.

Any suggestions?

---

### Post by bowens44 on 2009-03-14
dmesg output relevent to this issue:

[61983.996300] bttv0: timeout: drop=1305 irq=9349274/9349275, risc=3093b884, bits: HSYNC OFLOW
[61984.532299] bttv0: timeout: drop=1319 irq=9349321/9349322, risc=30f1d9f4, bits: HSYNC OFLOW
[61985.248300] bttv0: timeout: drop=1337 irq=9349384/9349385, risc=308e3904, bits: HSYNC OFLOW
[61985.800297] bttv0: timeout: drop=1351 irq=9349432/9349433, risc=30f1d9fc, bits: HSYNC OFLOW
[61986.332294] bttv0: timeout: drop=1365 irq=9349479/9349480, risc=3093b8bc, bits: HSYNC OFLOW
[61986.868300] bttv0: timeout: drop=1379 irq=9349526/9349527, risc=30f1da24, bits: HSYNC OFLOW
[61987.520296] bttv0: timeout: drop=1394 irq=9349589/9349590, risc=379a0020, bits: HSYNC OFLOW
[61988.836303] bttv0: timeout: drop=1421 irq=9349705/9349706, risc=308e38dc, bits: HSYNC OFLOW
[61990.204296] bttv0: timeout: drop=1455 irq=9349826/9349827, risc=30f1a8d4, bits: HSYNC OFLOW
[61990.756791] bttv0: timeout: drop=1469 irq=9349874/9349875, risc=3093ba1c, bits: HSYNC OFLOW

---

