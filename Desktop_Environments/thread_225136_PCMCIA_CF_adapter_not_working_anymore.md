---
title: "PCMCIA CF adapter not working anymore?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by jude999 on 2006-07-29
Hi all,

My pcmcia compact flash card adapter used to work like a charm. When I inserded the card, I had access to my files and could play with them.

But for some reason, it doesn't work anymore, when I plug the gard, nothing happens, no window opens, no link on the desktop... 

What's wrong?

here is what my dmesg says when I plug the card in:

```
[17193499.424000] pccard: PCMCIA card inserted into slot 0
[17193499.424000] cs: memory probe 0xe0000000-0xefffffff: excluding 0xe0000000-0xe07fffff 0xe2000000-0xe5ffffff
[17193499.436000] pcmcia: registering new device pcmcia0.0
[17193500.524000] Probing IDE interface ide2...
[17193500.812000] hde: SAMSUNG CF/ATA, CFA DISK drive
[17193501.148000] ide2 at 0xc080-0xc087,0xc08e on irq 3
[17193501.148000] hde: max request size: 128KiB
[17193501.148000] hde: 4097520 sectors (2097 MB) w/0KiB Cache, CHS=4065/16/63
[17193501.148000] hde: cache flushes not supported
[17193501.148000]  hde: hde1
[17193501.152000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0
```

---

### Post by jude999 on 2006-07-30
Anybody? Help. Please?

---

### Post by jude999 on 2006-08-02
Bumping 1 last time, somebody has to have an answer!

---

