---
title: "NWN neverwinter nights on wine with proprietary ATI graphics drivers"
date: 2014-03-25
forum: Gaming &amp; Leisure
---

### Post by vanquishedangel on 2014-03-25
I got Neverwinter nights 1 to work in wine!

The reason for doing this is the native linux installer is getting very old and requires a ton of tinkering around to work. Many of the libs needed for the native installer no longer are supported in newer ubuntu versions.

I use playonlinux for most things wine, but this fix should work for native wine (I havent tried it). You will need a copy of NWN1 and to run the script from playonlinux, I used the GOG version. Then install nwn normally. If you have proprietary ATI drivers nwn will attempt to start up but will fail. To fix this you need to go into the nwn directory and rename nwmain.exe to something else, I named mine to nwmain2.exe. Then you need to create a short cut to your newly named .exe (nwmain2.exe in my case). now you can play nwn1 in wine.

The reason that I have found for this is because when you are using ATI proprietary drivers, it recognizes the nwmain.exe and sets its own graphics settings, these settings are not compatible with wine. When you rename the file ATI will not recognize the new nwmain2.exe, and will leave the settings alone.

---

