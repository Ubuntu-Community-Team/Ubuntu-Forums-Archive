---
title: "Wine Errors when trying BF2142"
date: 2007-02-28
forum: Gaming &amp; Leisure
---

### Post by Nexusx6 on 2007-02-28
Hey all,
I tried finding my answers in the Wine forums and through google, and though other people have reported this problem.. no one has been able to help them, so I come to gamers of Ubuntu.

System Specs at a glance are
AMD 3200+
nVidia 6800
1 gig ram
Ubuntu Edgy 6.10

I've been trying to get BF2142 running on my system using Wine 9.31. People have reported various results in getting it to work in game, but for me it crashes after the splash screen with this error:

> 
wine "c:/Program Files/Electronic Arts/Battlefield 2142/BF2142.exe"
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
err:seh:raise_exception Unhandled exception code 80000003 flags 0 addr 0x4065a1
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00                                                                                                                                               000060,0x7d6b6468,0x54909a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00                                                                                                                                               000060,0x198e08,0x54909a): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00                                                                                                                                               0002cc,0x7d6b6468,0x54a772): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00                                                                                                                                               0002cc,0x198e08,0x54a772): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


I apperciate any help. I haven't had the chance to try Wine with anything else, so I don't know if this is a problem with just BF2142, or if this will be coming up for anything I run in wine.

Thanks :)

---

