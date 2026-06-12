---
title: "ata1 crashing"
date: 2009-04-19
forum: General Help
---

### Post by maybeway36 on 2009-04-19
I have two hard drives in my computer. One of them, when I leave the computer on for a long time, starts to make clicking noises and sounds like it can't read the disk. My computer then crashes if I try to do anything, even Ctrl+Alt+F1. When I rebooted to an Ubuntu live CD, it gave me errors involving ata1:
```
[   13.856017] ata1: SRST failed (errno=-16)
[   23.856017] ata1: SRST failed (errno=-16)
[   59.696057] ata1.01: cmd c0/00:00:00:00:00/00:00:00:00:00/f8 tag 8 dma 4896 in
[   59.696068]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   59.696167] ata1.01: status: { DRDY }
```
It then leaves me at a Busybox prompt. Strange... I thought it was the hard drive having problems...
If I leave the computer off for a while, it seems to work fine again.
What could be causing this problem, and which hard drive is it on?

---

