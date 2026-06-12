---
title: "Mounting Sony Memory Stick"
date: 2005-12-24
forum: General Help
---

### Post by Sebby on 2005-12-24
I have a Sony VAIO FS215S notebook with a built-in Sony Memory Stick reader. How do I go about mounting it?

I have had a search, but nothing has helped me so far.

Many thanks and Merry Christmas. :KS

---

### Post by hajk on 2005-12-24
Well, I would say plug it in and have a look at what happens in syslog and messages (menu Applications/System Tools/System Log etc.). Is it recognized as a SCSI devive (like /dev/sda1), or what? Check the output of the "lspci" command and see what it says about the reader. At least, that information will get you going in finding a solution...

---

### Post by Sebby on 2005-12-24
There is nothing in System Log. If I do lspci, this is what I see that relates to the card reader:

```
0000:06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:06:03.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
```

---

### Post by Sebby on 2005-12-26
Any ideas?

---

