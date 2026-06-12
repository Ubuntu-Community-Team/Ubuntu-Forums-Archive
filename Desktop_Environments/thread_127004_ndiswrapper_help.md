---
title: "ndiswrapper help"
date: 2006-02-07
forum: Desktop Environments
---

### Post by madddonkey255 on 2006-02-07
I downloaded a driver for my wireless card (D-link G630) from the Dlink website and when I try to install it with ndiswrapper I get the error message:
> Parse error in inf. Unable to find section W8100PCI.zerocfg
Parse error in inf. Unable to find section W8100PCI.zerocfg
Parse error in inf. Unable to find section W8100PCI.zerocfg

After this when I run ndiswrapper -l I get
> Installed ndis drivers:
mrv8k51 driver present, hardware present

but when I go to Networking to configure it or run ifconfig it doesn't show up.  I've been trying for awhile now to get it working and I'm not sure now what to do.
Thanks,
Nolan

---

### Post by adi-beg on 2006-02-08
```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

If you get errors after first line, driver was not installed.
You need second line if you want to load ndiswrapper automaticaly in boot.

Good luck.

---

### Post by queenorych on 2006-02-08
If you are using ndiswrapper from breezy you may want to download and install the latest ndiswrapper directly from the kind people at ndiswrapper.  There are a bunch of howto's.  There is even on on their website for ubuntu.

---

### Post by vishnukv on 2006-03-11
Hello, Sorry this is a long time, but I just configured DWL-G630 on breezy so thought I should post. I got the same error messages after installing WINXP MRV8K51.INF driver. I tried WIN2K driver and it installed like a charm. I would suggest trying the WIN2K driver. 
Then I just did 

sudo modprobe ndiswrapper
sudo ndiswrapper -m

My network card is detected automatically and it is working.
Thanks

---

