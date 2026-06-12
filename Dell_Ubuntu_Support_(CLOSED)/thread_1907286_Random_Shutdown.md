---
title: "Random Shutdown"
date: 2012-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Trevorius on 2012-01-11
I have a brand new Dell Vostro laptop with specs as follows

Processor 	2nd generation Intel Core i5-2430M (2.40 GHz Turbo Boost 2.0 up to 3.00)
Operating System	Dual boot Kubuntu 11.10 +  Windows 7 Professional 64bit 
Display	17.3 inch High Definition LED Display (1600 X 900)
Memory3	6GB3 Dual Channel DDR3 SDRAM at 1333MHz
Hard Drive 	500GB4 SATA hard drive (7200RPM)
Optical Drive 	8X DVD+/-RW with double-layer DVD+/-R write capability
Video Card	NVIDIA GeForce GT 525M (128-bit), 1GB Graphics

I just got it in December and for the most part things are working well a few small glitches but the one thing that's really starting to bug me is that every day or two the system seems to randomly turn itself off. Not like a crash, but when it happens when I'm there, the prompt comes on the screen as if I clicked the shutdown button from the start menu and it counts down from 30 seconds and I can click cancel if I catch it in time. But when I'm not there I come back and find it off.

I usually leave it on most of the time and this keeps happening but I don't even know where to start in searching for the cause. I don't notice any pattern like the length of time between shutdowns as it seems like I can walk away for 10 minutes and come back to find it off or I can be at work for 10 hours and everything is still fine. I tried checking /var/log/syslog and didn't notice anything unusual.

Any ideas?

---

### Post by Trevorius on 2012-01-14
I think I've figured out what is causing the shutdowns. The bit torrent client Ktorrent has an auto shutdown feature which gives the option of shutting down the computer under certain circumstances such as once all torrents have finished downloading. 

This feature had gotten clicked to "on" without me realising or intending to do so.  :confused:

---

