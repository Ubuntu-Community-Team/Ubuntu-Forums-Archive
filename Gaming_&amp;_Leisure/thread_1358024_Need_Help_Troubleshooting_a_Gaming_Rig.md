---
title: "Need Help Troubleshooting a Gaming Rig"
date: 2009-12-17
forum: Gaming &amp; Leisure
---

### Post by deamon_knight on 2009-12-17
I'm trying to get some games set up on a system, specifically Civ4 Beyond The Sword and UT2004. These games are a bit older but so is the hardware I'm using, mostly stuff I've collected from friends who were disposing of it. I've testing and I'm confident the hardware is not malfunctioning. Here are the Specs;
3GHZ Celeron, 1GB DDR RAM, ATI Radeon 9600, Chipset Intel 865PE.

I've discovered that ATI has moved the 9600 to "legacy" support. Version of Ubuntu after 8.04 don't locate ATI's drivers and use open source ones. While I can enable desktop effects, I cannot Launch Civ4 in WINE. I've successfully setup Civ4 with WINE and WINE Tricks on another system using WINE 1.1.31, (the Beta WINE version in Karmic). However, on this system it launches Civ4 (in Karmic or Linux Mint 8), but crashes. The game starts, the startup movies begin and the configuration menus load and can be navigated, the actual game engine fails to load, and crashes with an error, "out of shaders" or similar. I assumed that UT2004 would also not work without the ATI drivers, so I loaded 8.10 live and had the same difficulty finding drivers. I reverted to 8.04 Ubuntu (actually Linux Mint 5) and while it does load ATI's drivers, and I can successfully install WINE 1.1.31 and Launch Civ4, the display is corrupted and unreadable. This is true even after closing Civ4 and requires restarting X. Can anyone advise me how to proceed from here? I don't know if the problem is Civ4, WINE, ATI or Ubuntu or Linux Mint, I'm stumped.

I guess I'm not sure if I need the ATI drivers, to play games? (I think so), If there is any way to use those drivers in 8.10? (I don't think s but I don't understand why not). If there is some other reason why WINE 1.1.31 won't work in 8.04 or If using Linux Mint could be the problem somehow, or if its something else I've overlooked entirely.

Any help is appreciated!

---

### Post by n0glu3 on 2009-12-17
The open source drivers pretty much don't work with WINE.

---

