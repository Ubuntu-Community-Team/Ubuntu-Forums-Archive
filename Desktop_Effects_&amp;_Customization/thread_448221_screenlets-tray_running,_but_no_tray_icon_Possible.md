---
title: "screenlets-tray running, but no tray icon? Possible Panel bug"
date: 2007-05-18
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2007-05-18
[COLOR="Red"]**OOPS, sorry! Disregard this thread. All that was wrong was I accidentally removed the "notification area" from my panel**[/COLOR]

-----------------------------------------------------------------------------------

I installed xcompmgr and screenlets today, I have to say they're quite nice, especially for my old laptop with S3 twisterk graphics, 256mb of ram and athalon 4 900mhz processor.

anyway, screenlets-tray was working fine at first, but it was always being annoyingly placed to the right of my clock in the gnome panel, so i closed it, unlocked my clock and shoved it up against the right and did the same for all the others.

But now when i run screenlets-tray, I know its working properly because the screenlets daemon and the screenlets themselves are activated,** but the try icon never appears in the tray any more**. Command line output seems normal too:


```

screenlets-tray
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
CachingBackend: Loading cache ...
CachingBackend: Loading <SAFPJtojoTaKRvRf>
CachingBackend: Loading <4MB9Y1INo9fXPkwt>
Restore: <ClockScreenlet#4MB9Y1INo9fXPkwt>
import_and_create_screenlet: ClockScreenlet
Restore: <WeatherScreenlet#SAFPJtojoTaKRvRf>
import_and_create_screenlet: WeatherScreenlet

```

I'm thinking this is a strange panel bug, not a screenlets-tray bug. 

The only strange thing that happened to lead up to this is, as I was trying to push my clock up against the edge of the screen, i noticed there was some padding that kept it from being flush against the edge, then I realized there was a blank or null panel icon there, I was able to right-click it and remove it. I dont know if this was related to the issue or not, but it might be

---

