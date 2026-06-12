---
title: "m1330/Ubuntu 8.10 - Need help on performance problem"
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by antiOST on 2009-01-12
Hi

Need help on troubleshooting massive performance problem with 8.10 on M1330.

I have been running 7.10 (gutsy) the past year and it worked like a charm with dual-boot with WinXP and then the trouble began.

My Nvidia card broke down (the infamous overheating problem) but Dell support was fast and sent a technician to replace my motherboard.
Before the change I was running with BIOS version A10 after the change its A14.
After the change my ubuntu (still 7.10) started to freeze without notice, I tried several thing (updating and configuring xserver, nvidia etc. ) but no luck, so I decided to do an clean install to 8.10.

The upgrade went smooth. I have my home folder on another partition so I keep this without changes (don't know if this could mess things up)
But when I have been using the system for som time, ubuntu starts to react really really slow or even hangs at times espesially when watching movies seems to degrade the performance. Taking ages to swith windows.

I have tried installing Nvidia driver v.177 and I'm now using v.173, 173 seems to be a little better than 177 but can't say for sure. I also suspect it's a heating problem but cannot confirm this. The temparature can be as high at 47-48 Celcius (cat /proc/acpi/thermal_zone/*/*)
When running windows the heat is also high but I don't experience performance problems. The heat was also high before the new motherboard but I never experienced any performance problems (until of cause my graphics card went down)

I'm lost here and really need help on determine what is causing the problems.

- is it the new bios version?
- overheated nvida card (but then why no in windows)?
- someting incompitible between m1330 and 8.10 (should I try 7.10 or 8.04)?
- can I configure some performance counters og logs to find the problem?

I could of course call Dell Support but in my country Ubuntu isn't supported and my WinXP works fine!

Thanks
Kim

---

### Post by antiOST on 2009-02-18
I had an Dell technician to come by me today and changed the heatsink (fan). So far it seems to have solved the problem. The tempature is acceptable now and haven't had any freezes or slowness so far.

My laptop is now acting like before the first change of motherboard. I consider my problem solved

-Kim

---

