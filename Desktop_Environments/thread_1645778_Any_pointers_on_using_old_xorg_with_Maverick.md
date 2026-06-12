---
title: "Any pointers on using old xorg with Maverick?"
date: 2010-12-15
forum: Desktop Environments
---

### Post by anttir on 2010-12-15
Hi,

I need to use fglrx as later don't support TecraS1 chipset and ati driver is unable for FS flash playback.

The required ati fglrx only works with Dapper 6.06 LTS but not with new newer releases with newer xorg.

Please someone fix me on this. If I remember maverick xorg I lose all the ubuntu screen candy, right?  If I compile xorg7.0 with Maverick I guess I could get it to work, but what about getting Ubuntu Gnome desktop instead of plain out-of-the-box xorg?

Thanks on all advice.

---

### Post by Krytarik on 2010-12-15
Does your video chipset belong to the so-called "legacy" cards/chipsets?
Did you try the driver offered via "System -> Administration -> Additional Drivers", is that what you called "ati driver"?

I wouldn't try to downgrade the x-server to a level where the proprietary drivers build by ATI/AMD are still working. Instead, and that's apparently just the lesser evil, I would by a comparable Nvidia-card. Even after nine years I still can use the drivers build by Nvidia, but my mum with her just 5-year-old ATI-card has to rely on the os-community-build drivers, so-called "nouveau"-drivers. The performance of those is significant higher than of the generic drivers, but still don't reach that of the old ATI-developed proprietary drivers, hopefully they are getting better over time.

---

### Post by Krytarik on 2010-12-16
> **Krytarik said:**
> Does your video chipset belong to the so-called "legacy" cards/chipsets?
Did you try the driver offered via "System -> Administration -> Additional Drivers", is that what you called "ati driver"?

I wouldn't try to downgrade the x-server to a level where the proprietary drivers build by ATI/AMD are still working. Instead, and that's apparently just the lesser evil, I would by a comparable Nvidia-card. Even after nine years I still can use the drivers build by Nvidia, but my mum with her just 5-year-old ATI-card has to rely on the os-community-build drivers, so-called "nouveau"-drivers. The performance of those is significant higher than of the generic drivers, but still don't reach that of the old ATI-developed proprietary drivers, hopefully they are getting better over time.
The "Nouveau"-drivers are for Nvidia-cards, the open-source ATI-drivers are called "Open Source Edge", sorry.
And they can be installed this way: [http://wiki.cchtml.com/index.php/Ubu...e_Edge_Drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers") , not the way mentioned above.

---

### Post by anttir on 2010-12-17
> **Krytarik said:**
> Does your video chipset belong to the so-called "legacy" cards/chipsets?
Did you try the driver offered via "System -> Administration -> Additional Drivers", is that what you called "ati driver"?

I wouldn't try to downgrade the x-server to a level where the proprietary drivers build by ATI/AMD are still working. Instead, and that's apparently just the lesser evil, I would by a comparable Nvidia-card. Even after nine years I still can use the drivers build by Nvidia, but my mum with her just 5-year-old ATI-card has to rely on the os-community-build drivers, so-called "nouveau"-drivers. The performance of those is significant higher than of the generic drivers, but still don't reach that of the old ATI-developed proprietary drivers, hopefully they are getting better over time.


hi,

thanks for the insight.

The laptop graphic chipset is Mobility 9000 (RV250?). It's not supported neither the fglrx provided with Lucid/Maverick nor with the latest fglrx from ati.

I checked your links and seems the radeonhd does not support older cards. The radeon driver provided with maverick/lucid apparently is [xf86-video-ati]("http://www.x.org/wiki/RadeonFeature") and it was slow. According to [http://www.x.org/wiki/RadeonFeature ]("http://www.x.org/wiki/RadeonFeature")the R100-R200 models "video decode" support is TODO. That would explain the slowness with Tube.

I don't think unstalling xorg would be good start as it uninstalls whole ubuntu desktop. Rather I could try compiling some binaries from older sources and replace binaries respectfully. Seems like a tough job though. But I already got FF3.6.13+flash10 with Dapper and that too wasn't too simple.


Thanks :)

---

### Post by Krytarik on 2010-12-17
> **anttir said:**
> I don't think unstalling xorg would be good start as it uninstalls whole ubuntu desktop. Rather I could try compiling some binaries from older sources and replace binaries respectfully. Seems like a tough job though. But I already got FF3.6.13+flash10 with Dapper and that too wasn't too simple.
Stop, the old drivers don't support the recent xorg-xserver (only up to 7.4), so I doubt that even if compiling the binaries on your own you will get them working!

Indeed I don't see why the open-source radeon driver would not support your card:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

You should also try the "Open Source Edge"-drivers.

---

### Post by anttir on 2010-12-19
> **Krytarik said:**
> Stop, the old drivers don't support the recent xorg-xserver (only up to 7.4), so I doubt that even if compiling the binaries on your own you will get them working!

Indeed I don't see why the open-source radeon driver would not support your card:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

You should also try the "Open Source Edge"-drivers.

Ok, I updated the situation.
I tried both updated Lucid and updated Maverick but the radeon driver provided with those systems were no good. It does support the Mobility9000 driver in a limited way but it was so much slower that FS-flash didn't  work. Maybe if I had faster core2 processor this would not be my problem anymore.

I had a look on the "Open Source Edge" driver but it is only for R300+ (Radeon 9500->). 
From ccwiki Lucid page:
"**Which cards do ATI no longer support?** The ATI Radeon 9500-9800, Xpress200-1250, 690G, 740G, X300-X2500  (including Mobility RadeonHD 2300, since it is really a DirectX 9 part).   See the complete list [here.]("http://wiki.cchtml.com/index.php/9.4") If your card is on that list, you are limited to open-source drivers on  Ubuntu Lucid. If you really need the proprietary Catalyst/fglrx driver,  you will have to use an older Linux distribution, such as Debian  Lenny/5.0.x or Ubuntu Hardy/8.04.x."

I'm somewhat disappointed that the Radeon9000 is not even in the "Deprecated" list, it starts with Radeon 9500 :p

---

### Post by Krytarik on 2010-12-19
I was very disappointed either that the drivers provided by AMD/ATI doesn't support the video card I've installed at my mums pc anymore, just after 5 years! I buy no video cards from AMD anymore.

---

