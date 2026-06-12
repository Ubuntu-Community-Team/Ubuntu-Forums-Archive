---
title: "resolution changes on reboot"
date: 2006-01-10
forum: Desktop Environments
---

### Post by quiv on 2006-01-10
I have just installed Ubuntu 5.10 a few days ago. I noticed that after restarting the box, sometimes ubuntu is stuck in 640x480 resolution, with no option to change it, Whereas other times it starts correctly in my desired resolution and refresh (1280x1024 @ 85 hz). 

The only thing i can think of is that I have a KVM switch (Belkin OmniCube), and perhaps if I don't have the ubuntu box active on the KVM, it defaults to 640? Has anyone else experienced this? 

Thanks!

---

### Post by egar on 2006-01-17
I have exactly the same problem using Dapper.  Sometimes it boots at 640x480.  Then I reboot and it's my normal 1152x864.  I haven't found a pattern as to why it works sometimes and not others, only that booting at 640x480 seems to be happening more often.

---

### Post by RAOF on 2006-01-17
[QUOTE=quiv]...
The only thing i can think of is that I have a KVM switch (Belkin OmniCube), and perhaps if I don't have the ubuntu box active on the KVM, it defaults to 640? Has anyone else experienced this? 

Thanks![/QUOTE]
That could well be it - when X (the GUI server) starts, it'll ask the monitor what sort of resolutions/refresh rates it can support.  If the monitor's not connected, it'll assume the worst and use the safest (ie: lowest possible) resolution/refresh rate.  Possibly.

---

### Post by egar on 2006-01-17
I found my problem, the horizontal and vertical sync rates were missing from my xorg.conf file.  Apparently it's been that way since I last built my system, because I backup config files for the initial install and they also were missing the setting.  Packages contained in later upgrades to my system must have not been as tolerant of the missing sync rates as the older packages.

---

