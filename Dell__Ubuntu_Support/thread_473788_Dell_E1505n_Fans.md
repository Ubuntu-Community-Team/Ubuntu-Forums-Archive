---
title: "Dell E1505n Fans"
date: 2007-06-14
forum: Dell  Ubuntu Support
---

### Post by fjgaude on 2007-06-14
It's a hot day here... computer fans came on when the THRM of GKrellM showed 68C. Temp quickly went down to 62C, then the fans shut off when the temp reached 56C. Seems like all works correctly with Ubuntu as shipped from Dell.

The temp was that high because of heavy notebook computer use. I stopped my activity when I heard the fans come on just to see how things were going to go. The fans are powerful enough to keep the temp below 70C. I'm not sure where the measurement is actually made in computer, only Dell knows. <smile>

frank

---

### Post by neptho on 2007-06-15
Many of these are BIOS settings.  You can install and use the i8k utilities to manually toggle the fans on and off, and [run the i8kmon daemon to manually turn them on if you wish to override the defaults](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans).

With the A15 BIOS on my 6400, my fans are set to happily kick on at the lowest setting at 45c, and go nuts at 50c (It's very humid, and that does have a bit more of an effect on the system.)

I assume there wasn't actually a question here?

---

### Post by fjgaude on 2007-06-15
No question, as the way my 1505 was setup at the factory is just right. The fans are very quiet, can hardly hear them. But of course, I've never had the temp go over about 72C.

I will install the i*k files and see how they work. Thanks for the tip.

frank

---

