---
title: "Problems with Ubuntu-start"
date: 2005-11-08
forum: Desktop Environments
---

### Post by dedalus on 2005-11-08
Hi, 

I have problems with my Ubuntu-start. It stops when the ubuntu splash appears. Then my PC waits 50 seconds before the starting process is going on. At this moment the splash disappears and ubuntu is starting in textmodus. In the 50 seconds break the screen doesn't change.

here is a bootchart:
[http://home.arcor.de/j0sch/bootchart.png]("http://home.arcor.de/j0sch/bootchart.png")

I hope you can help me

Cheers

---

### Post by dedalus on 2005-11-09
hi,
here is a log file. The break comes after/while searching ide4, but i dont't habe an ide4. Is there anything I could do?

Cheers


Code:

... 
Nov  8 22:00:05 localhost kernel: [4294671.035000] Probing IDE interface ide1... 
Nov  8 22:00:05 localhost kernel: [4294671.707000] hdc: TOSHIBA DVD-ROM SD-R2212, ATAPI CD/DVD-ROM drive 
Nov  8 22:00:05 localhost kernel: [4294672.319000] ide1 at 0x170-0x177,0x376 on irq 15 
Nov  8 22:00:05 localhost kernel: [4294672.319000] Probing IDE interface ide2... 
Nov  8 22:00:05 localhost kernel: [4294672.832000] Probing IDE interface ide3... 
Nov  8 22:00:05 localhost kernel: [4294673.345000] Probing IDE interface ide4... 
Nov  8 22:00:05 localhost kernel: [4294708.015000] ide4: Wait for ready failed before probe ! 
Nov  8 22:00:05 localhost kernel: [4294708.525000] Probing IDE interface ide5... 
...

---

