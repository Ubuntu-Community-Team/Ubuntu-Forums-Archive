---
title: "PCMCIA CF card adaptor doesn't work"
date: 2005-04-18
forum: Desktop Environments
---

### Post by vtrac on 2005-04-18
I have an IBM Microdrive that came with a PC Card (PCMCIA) card adaptor that I use to trasfer files from my digital camera to my computer.  It is one of the last things I can't get working in Linux that prevents me from using linux 24/7.  It appears to be an IRQ conflict.  This is the relevant dmesg output:
> Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
Probing IDE interface ide2...
ide-cs: ide_register() at 0x100 & 0x10e, irq 10 failed


And this is the relevant output from /var/log/messages:
> Apr 18 10:58:12 localhost kernel: ide-cs: ide_register() at 0x100 & 0x10e, irq 10 failed


Any ideas?

---

### Post by Randar on 2005-12-09
I have the same problem with the same IBM drive, but I am using Ubuntu 5.10. Should I start a new thread?

---

