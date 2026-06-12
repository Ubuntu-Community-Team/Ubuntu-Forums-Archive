---
title: "x server"
date: 2006-05-13
forum: Desktop Environments
---

### Post by Koech on 2006-05-13
I'm new to Ubuntu and Linux. My motherboard is a GeneratioNext(Genx) with a VIA/S3G Unichrome Pro IGP driver. I've tried running Ubuntu live with no success I get a msg that the x server failed to start. By default it uses vesa but it doesn't work. I've tried via, s3 and vga with no success either. Please help.:confused:

---

### Post by calm user on 2006-05-19
I have the same problem. Used the live cd in a Dell 8400, LGA775, 925X, ATI X800 box. Funny thing, I had no problem on a much older 'orphaned' PC (AMD K-6+, BCM mobo - Sis chipset). What exactly does the error message mean?

Failed to start X server (graphical interface)
Would you like to view output? <Yes>
-bash: no job control in this shell ubuntu@ubuntu: ~$

TIA

---

### Post by calm user on 2006-05-19
Additional info for above:
3.0Ghz Prescott core LGA 775
2Gb DDR2 SDRAM PC-4300
USB Optical mouse
ATI X800 128Mb
Creative Audigy 2 ZS
Maxtor SATA 80Gb HDD
PCI-X mobo
2 Optical drives (CD-RW, DVD +/-DL)
350W PSU

Trying out Ubuntu 5.10 (Breezy?)

---

### Post by i++ on 2006-05-19
I had the same problem with ubuntu 5.10 breezy install, it wouldn't run x server. I had to edit the xorg.conf file and change the gfx driver to "radeon" instead of "ati" and this solved the problem for me... it just uses a different driver.

---

### Post by calm user on 2006-05-20
Thanks for your reply. I poked around on the web and what I found in common was the error was most prevalent in systems with ATI graphics.

[http://www.control-escape.com/linux/x.htm](http://www.control-escape.com/linux/x.htm) 

That helped in narrowing down it being a display driver issue.

[http://www.perspectives.com/forums/view_topic.php?id=81572&forum_id=68](http://www.perspectives.com/forums/view_topic.php?id=81572&forum_id=68)

That narrowed it down to the ATI card being the culprit.

I hope this helps others. By the way, I'll keep your reply handy as you have the same vid card as me.

---

