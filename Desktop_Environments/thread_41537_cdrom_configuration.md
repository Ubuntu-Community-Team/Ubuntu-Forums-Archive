---
title: "cdrom configuration"
date: 2005-06-13
forum: Desktop Environments
---

### Post by eray on 2005-06-13
All,

I apologize in advance for such a basic post but I am new to Linux. I installed Hoary and configured it without any issues. However, I recently replaced my old CDROM because it was acting up. The new CD was detected FX3210S and seems to work well.. until you try to play music. The CD player kicks off and all seems well but if you listen it is skipping constantly... jumping forward and back. You can make out the music but it is unusable. I have looked high and low and can not seem to find any instruction on how I can tweak the config to make this work correctly. Here is that portion of my dmesg:


Probing IDE interface ide1...
hdd: FX3210S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...

Thanks in advance.

---

### Post by diebels on 2005-06-13
Needs dma maybe?

---

### Post by jarrett.wold on 2005-06-18
Check out:  man hdparm

You can tweak DMA and a bunch of other stuff as well.

---

