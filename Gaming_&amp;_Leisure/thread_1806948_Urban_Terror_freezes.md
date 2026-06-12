---
title: "Urban Terror freezes"
date: 2011-07-18
forum: Gaming &amp; Leisure
---

### Post by Juliolp on 2011-07-18
Hi! I got a Medion MT7 MT409G:

Intel Pentium 4 2,66GHz with 512MB DDR2 Ram with a Motherboard MS-7222

I made an Ubuntu 11.04 fresh installation.

Ubuntu goes very fast with Gnome, and i downloaded Urban Terror. The game start -I use the linux executable-, i can choose server, loads the map, but when it started, with a good sound too, good move, etc. in a  few seconds it freezes and the sounds are off.

I can't move the mouse and i only can turn off the PC and start again.

Maybe i don't have the minimum requeriments to play URT? Or i can do something to improve performance and play?

Thanks very much.

---

### Post by Perfect Storm on 2011-07-18
Which video card do you have?

---

### Post by Juliolp on 2011-07-19
> **Artificial Intelligence said:**
> Which video card do you have?
Hi! I used the lspci command in terminal and i found these:

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 7222
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f4000000 (32-bit, prefetchable) [size=64M]
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fc000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: viafb

I hope these can help you to guide me , im newbie in Ubuntu but i love it!! Thanks very much. :D

---

### Post by Perfect Storm on 2011-07-19
I'm afraid that your video card isn't sufficient for playing Urban Terror. S3 cards are a poor choice if you want to game (plus linux S3 drivers aren't as good as the Windows counterpart), if you can get your hand on a used Nvidia card for 3D games, as I doubt you can get a new one to a P4 computer.

---

