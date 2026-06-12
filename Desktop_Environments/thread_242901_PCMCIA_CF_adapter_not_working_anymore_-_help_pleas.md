---
title: "PCMCIA CF adapter not working anymore - help please"
date: 2006-08-24
forum: Desktop Environments
---

### Post by jude999 on 2006-08-24
Hi all,
I have a PCMCIA adapter for my CF card that used to work great, but it doesn't anymore.

My dmesg tells me this:
```
[17179868.512000] pccard: PCMCIA card inserted into slot 0
[17179868.512000] cs: memory probe 0xe0000000-0xefffffff: excluding 0xe0000000-0xe07fffff 0xe2000000-0xe5ffffff
[17179868.524000] pcmcia: registering new device pcmcia0.0
[17179868.804000] Probing IDE interface ide2...
[17179869.092000] hde: SAMSUNG CF/ATA, CFA DISK drive
[17179869.428000] ide2 at 0xc080-0xc087,0xc08e on irq 11
[17179869.428000] hde: max request size: 128KiB
[17179869.428000] hde: 4097520 sectors (2097 MB) w/0KiB Cache, CHS=4065/16/63
[17179869.428000] hde: cache flushes not supported
[17179869.428000]  hde: hde1
[17179869.432000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0
```

What is the problem?

---

### Post by jude999 on 2006-08-24
help, anyone?

---

