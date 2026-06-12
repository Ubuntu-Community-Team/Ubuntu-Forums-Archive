---
title: "AMD Catalyst Control Center Shows Monitor ID at Boot"
date: 2012-05-27
forum: Desktop Environments
---

### Post by mdmcaf on 2012-05-27
Hey y'all~

I've been experiencing a problem with my Xubuntu 11.04 build wherein the monitor identification tabs appear on the desktop whenever I log into my computer after it's been hibernating. The problem doesn't seem to occur every time I log in from a cold start, though it has happened.

I've waited about 45 sec - 1 min for the icons to go away but they never do. I have to open a terminal, open AMD Catalyst Control Center with the sudo command, and click on the icon labeled "Identify Display" to make the icons go away. It doesn't matter if I change it to auto-hide, whenever I log back into the computer from a hibernation state the icons reappear as though I'd never clicked on the option in the first place.

It's not a huge deal, just annoying.

I don't like to turn off my computer at night when I'm done working on it, I prefer to hibernate it because then I get all of my windows back (most importantly the terminal sessions) in the exact state that I left them and the boot is quicker. I haven't tested powering the machine off too much because of this, though I have noticed that when a power down or restart is necessary (such as when installed updates require a restart) the icons don't always appear.

Any ideas would be splendid.

I have a laptop (a ThinkPad x100e) running Xubuntu 12.04 which I also hibernate at night (it's configured to hibernate when I close the lid) and the problem isn't present. The ThinkPad also has an AMD graphics card. I don't have any machines with Nvidia graphics cards with which to test.

I should also note that the system in which this occurs is running an XFX Radeon 6870 1GB card and has three monitors attached to it; a 27" Dell U2711 display connected to the Dual-Link DVI connector, a 24" Dell P2411H connected to a DVI connector, and a Dell 20" 2009W monitor connected to the mini display port via an active mini display port to DVI adapter. I occasionally have problems with the 24" P2411H monitor not displaying at its full resolution when starting from a powered-down state, which messes up the rest of the monitor configuration and I, again, have to enter the CCC in order to set the 24" monitor at its correct resolution. This has not happened in some time.

Thanks.

---

