---
title: "[SOLVED] HP printer Problem Hardy Heron"
date: 2008-09-16
forum: Desktop Environments
---

### Post by dartrod on 2008-09-16
Hi, I am having trouble printing to my HP 845C printer.  When I attached this printer to my PC, Hardy Heron recognized the printer and installed the driver.  However, when I try to print, I get gibberish and one line per page.

Any help would be appreciated.

My hardware configuration is as follows:

AMD Athelon 64 LE 1640 2.6 GHZ 45 watt L2-1MB AM2
AMD Athelon 64 original Stock Fan and Heatsink
Kingston DDR2 PC2-5400 1GN/667 MHz
BIOSTAR MCP6P-M2 (NVIDIA GF6150, SATAII, RAID, DDR2-800
NVIDIA GeForce 6150 GPU Memory share upto 512MB
Onboard High Definition Audio
Onboard Network Card
450W ATX Power Supply
Western Digital CaviarSE 160GB 7200RPM SATA

---

### Post by fballem on 2008-09-16
> **dartrod said:**
> Hi, I am having trouble printing to my HP 845C printer.  When I attached this printer to my PC, Hardy Heron recognized the printer and installed the driver.  However, when I try to print, I get gibberish and one line per page.

Any help would be appreciated.

My hardware configuration is as follows:

AMD Athelon 64 LE 1640 2.6 GHZ 45 watt L2-1MB AM2
AMD Athelon 64 original Stock Fan and Heatsink
Kingston DDR2 PC2-5400 1GN/667 MHz
BIOSTAR MCP6P-M2 (NVIDIA GF6150, SATAII, RAID, DDR2-800
NVIDIA GeForce 6150 GPU Memory share upto 512MB
Onboard High Definition Audio
Onboard Network Card
450W ATX Power Supply
Western Digital CaviarSE 160GB 7200RPM SATA

If you are running HPLIP, then please check your version number. Please refer to the attached screenshot.

If you are running GNOME, then the icon for HPLIP should be in the upper-right corner of the upper panel. Right-click on the icon, then select HP Device Manager. That should open a screen similar to the left screen on the screen shot. If you select Help | About, then that should show the screen on the right. The screen on the right will identify the version number.

The version that is in the repositories is 2.8.2. The current version is 2.8.7. Each version seems to fix a number of problems, so it might be worth replacing HPLIP, assuming that's what you are using.

Please let us know, and if necessary, I can walk you through the process of replacing the outdated HPLIP.

---

### Post by dartrod on 2008-09-17
> **fballem said:**
> If you are running HPLIP, then please check your version number. Please refer to the attached screenshot.

If you are running GNOME, then the icon for HPLIP should be in the upper-right corner of the upper panel. Right-click on the icon, then select HP Device Manager. That should open a screen similar to the left screen on the screen shot. If you select Help | About, then that should show the screen on the right. The screen on the right will identify the version number.

The version that is in the repositories is 2.8.2. The current version is 2.8.7. Each version seems to fix a number of problems, so it might be worth replacing HPLIP, assuming that's what you are using.

Please let us know, and if necessary, I can walk you through the process of replacing the outdated HPLIP.
Hi, thanx for the reply, I checked my version of HPLIP and it is 2.8.2.

Any further help would be appreciated

---

### Post by dartrod on 2008-09-17
> **dartrod said:**
> Hi, thanx for the reply, I checked my version of HPLIP and it is 2.8.2.

Any further help would be appreciated
Sorry the version is 2.8.7

---

### Post by dartrod on 2008-09-17
> **dartrod said:**
> Sorry the version is 2.8.7
More info

When I print a test page from HPLIP it prints fine when I print from the test editor or from Open Office I just get gibberish and one line per page.

---

### Post by dartrod on 2008-09-17
> **dartrod said:**
> More info

When I print a test page from HPLIP it prints fine when I print from the test editor or from Open Office I just get gibberish and one line per page.
Problem Solved.  When I originally installed the printer I didn't have HPLIP installed. I installed HPLIP later.  I removed the printer though the Printer configuration utility. and re-installed it using HPLIP and every thing is fine now

Thanx for your help

---

### Post by fballem on 2008-09-17
You're welcome. I especially like problems that solve themselves, but I hope that my small contribution was useful.

Please don't forget to use the Thread Tools to mark this thread solved. That way, other users (including me) can benefit from your experience.

Thanks,

---

