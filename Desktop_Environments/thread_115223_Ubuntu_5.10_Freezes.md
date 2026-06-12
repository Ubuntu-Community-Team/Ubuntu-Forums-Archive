---
title: "Ubuntu 5.10 Freezes"
date: 2006-01-10
forum: Desktop Environments
---

### Post by hsn on 2006-01-10
Good afternoon folks,

First, i'm sorry for my bad English and i'm new to Linux Ubuntu.
2 Days ago I installed Ubuntu and it's great! But it crashed 2 times today, everything just froze and i had to press the reset button. When I reset the machine it wont boot and i have to turn of the computer and then turn it on again to make it boot.

It happend while i was downloading lots of files with firefox while using the plugin 'download them all', then I opened XMMS and a few sec later, it froze..

CPU: P4 2.8 @ 3.0
768MB DDR
200GB Maxtor
400W PSU
MOBO: ASUS P4p800-e Deluxe

Thanks in advance ;)

---

### Post by Gustav on 2006-01-10
If you have a NVIDIA card that might be the problem.

If so be sure to not have the line
```
option          "RenderAccel"
```
in your /etc/X11/xorg.conf because that has been known to cause freezes.

---

### Post by kaamos on 2006-01-10
Another possibility would be DMA related errors. You can check this by looking at the output of ```
dmesg | grep -i dma
```If you see a lot of timeouts and other suspucious things, this could be the cause..

---

### Post by hsn on 2006-01-13
Hi,

I have an Ati Radeon 9600 Card.

Right now i'm in windows xp. The strange thing is, after Ubuntu pissed me off (sorry), i installed Fedora Core 4, and had the same problem. But when the system froze, i couldn't boot linux anymore, grub gave some errors, and i had to install xp. Why's this?

---

