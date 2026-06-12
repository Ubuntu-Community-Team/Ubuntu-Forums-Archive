---
title: "Help! WoW and Wine performance"
date: 2010-09-19
forum: Gaming &amp; Leisure
---

### Post by an_oasis on 2010-09-19
Hi all, my old mobo died recently, so I replaced it and the processor and decided it was a good time to try out Ubuntu!  So far I am very impressed by the general speed, ease of use, and efficiency.  However, one of my pastimes is gaming and I found serious flaws herein.

I went through the guide here ( [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ) and successfully got WoW up and running on my machine, but it has serious performance issues.  I've gone through tons of forums and tried many things but haven't been able to find a cure, so please try to help!

My system:

Running Ubuntu 10.04 32bit
Screen: HP2207 22" wide 1650x1050 (prefers 60Hz refresh rate)
AMD Athlon II X4 640 Propus 3.0GHz Quad-Core
2.5GB DDR2 RAM @667
GeForce 9800GT 512MB ("current" driver)
320 GB Hitachi HD
ASUS M4A785-M AM3/AM2+/AM2 AMD 785G HDMI Micro ATX AMD Motherboard
Antec 650W PSU

I feel like this setup should be running WoW easily at high graphics settings, but I'm getting 2-6fps (40-60ms) on ICC25 boss fights at almost bare minimum graphics settings!

An oddity that I encountered was when going into the in-game Video settings and noticing that the "refresh rate" is either blank or "Fireball.wav", with the only other options being 82 and 83Hz. However, in the Config.wtf it has gxRefresh at 53Hz (it resets if i try to change it in the config.wtf).

Enabling opengl increases fps only very slightly and also causes a tiny bit of mouse cursor delay as expected (Yes, I know the mouse delay has a "fix"). Also, 75% of the time, when opengl is enabled, WoW crashes upon login.

On System Monitor, my CPU usage from Wow.exe rises to around 120% while playing, while all four cores seem to be around 50% load! I also play in maximized Windowed mode so I can alt+tab/change workspaces without Wine dying on me.

Additionally, as soon as WoW starts (on transition from launcher to full game), my sound dies completely and doesn't work again until I reboot.  I'm not sure this is Wine-specific because I also have this problem when starting Heroes of Newerth (they have a working linux client, if a little glitchy).

I'd really prefer not to go back to Windows, but not being able to play games would be enough of a hassle for me that I am pondering switching back, so any help would be greatly appreciated!

PS: I'm running through Wine (latest version, 1.2), though I've been poking around forums and heard about a more gaming-specific version of it called Cedega, not sure if it would make a significant difference.  Also, I'm worried about overclocking because I've never done so before and my memory isn't that great. I've also read reviews stating that the stock fan on the CPU is meh.

---

### Post by Drdog on 2010-09-20
I'm having the same problems (for the most part) and I too, am new to Linux. I hope we can find some answers! I've been to sooooo many forums, it's a little unnerving.

---

