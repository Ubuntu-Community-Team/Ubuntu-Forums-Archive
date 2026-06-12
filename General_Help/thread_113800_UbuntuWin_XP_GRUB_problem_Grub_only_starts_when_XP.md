---
title: "Ubuntu/Win XP GRUB problem: Grub only starts when XP setup CD is inserted..."
date: 2006-01-07
forum: General Help
---

### Post by staszek on 2006-01-07
A few weeks ago I installed Ubuntu on my laptop without any problems, and yesterday I thought that my desktop was ready for it as well. But this was a bit too optimistic...

I have three disk:
1. SATA: 1 partition with Wndows XP
2. IDE1: 1 partition with Ubuntu installed
3. IDE2: 2 partitions with music and pics only

I installed Ubuntu on IDE1 without problems, but after the first reboot Windows XP was started automatically. No GRUB boot menu was displayed.

Based on some forum search results, I booted from Ubuntu install CD and typed 'rescue'. After the prompt I typed: GRUB INSTALL /DEV/SDA

When I rebooted the computer (without Ubuntu CD), the boot process stopped and the display only shows "GRUB GRUB"
The only thing I can do at this moment is reboot, with the same result.
So now I had nothing: no Ubuntu, no Windows.

By coincidence I found out that when I boot the computer from the Windows XP setup CD, GRUB normally starts up and I can choose Ubuntu or windows and everything works perfect.

When I try to boot without the Windows XP setup CD, the same problem: 'GRUB GRUB'.

I tried to start up the recovery module from win XP and repair the MBR, but without result (my SATA drive is not recognised).

Please help me to solve this problem so I can move on with Ubuntu and stop myself from being dependent of Microsoft alone :) 

Thanks for your input!

Staszek

---

