---
title: "WLAN connection drops"
date: 2005-10-18
forum: Desktop Environments
---

### Post by hamil on 2005-10-18
I have been running on Breezy for some days now. In the beginning, it worked ok. But now my wlan connection keeps dropping out all the time. Sometimes it can be fine for hours, but then, like now, I can be online for 20 minutes, and the line drops without any warning at all...
I thought it may have something with the drivers used for my WG311v2 wlan adapter, so I read some manuals about NDISWrapper for my adapter.
30 minutes ago, I decided to give it a shot, but it did not work out allright...

I installed both the NDISWrapper-utils, and the gtk GUI.
My first try was with the GUI, I pointed it to the place where i have downloaded the drivers for it, at first the winXP driver "wg311v2.inf", and installed it. In the GUI, it then shows that it is no hardware present.....
I went back to terminal, and did the work manually, removed the installed driver, and reinstalled it. 
When running ndiswrapper -l, it shows that the driver is invalid.
I do not know how to get it working... I have tried the drivers for xp, me, 98 and 2000, without any luck. They all shows up as invalid drivers..

Any guesses to how I can make it work?

Brgds
Lasse

---

### Post by detour on 2005-10-18
[QUOTE=hamil]
Any guesses to how I can make it work?
[/QUOTE]

A few things:

1. I use the same card and breezy autoconfigured using acx111 drivers (module: acx_pci). This should be correct as the card uses a Texas Instruments chipset. You can see on this ndiswrapper [wiki page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N") that it is the preferred driver to use. That said, my connection with the acx111 drivers is also pretty choppy.

2. With Hoary, i used ndiswrapper and had the same connection issues. However, I can tell you that you that the xp driver inf that you initially installed is the correct one. Perhaps there's a conflict because you still have the acx111 driver installed. Try: sudo rmmod acx_pci  to remove it from memory, then sudo modprobe ndiswrapper.

3. I keep a simple python script (found somewhere on this forum) in my home directory that watches for a dropped connection and restarts networking. Save the attached file as fixnet.py. Open it in any text editor and modify the values of MYWIRELESSDEVICE and MYWIRELESSDRIVER to match your current configuration. Then open a terminal and enter: sudo chmod +x fixnet.py  use it by typing sudo python fixnet.py (leave that terminal open). There's a way to get it to start up when your system boots so that it runs quietly in the background but i can't remember how.

4. If all else fails, Linuxant is licensed by Texas Instruments to support their chipsets free of charge, so you could try their [WLAN DriverLoader]("http://www.linuxant.com/driverloader/") as well.

---

### Post by hamil on 2005-10-18
Thanks for the inputs.
I am running the python script now. Looking forward to see how it works.

Maybe I am lucky this time....

Lasse

---

### Post by hamil on 2005-10-20
Well, it turns out that I was that lucky at all...
My connection is even more unstable now...

Giving the Linuxant driver a shot, and praying for the best...

---

