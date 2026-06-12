---
title: "Wake from suspend/hibernate - black screen"
date: 2011-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Thule on 2011-04-29
Hi.

I have a dell precision M4400 with the following spec:
Precision M4400 : Intel Core 2 Duo P8400 (2.26GHz,1066MHz,3MB) 1 8.012,32 8.012,32 S
W11M4401 1 S
Base Option : 512MB Discrete nVidia FX770M Graphics Card (with 512MB dedicated memory) 1 S
Display : 15.4in Widescreen WXGA (1280X800) with CCFL lighting
Memory : 2048MB (2x1024) 800MHz DDR2 Dual Channel
Hard Drive : 320GB Serial ATA (5400 RPM) Hard Drive

Whenever I try to "wake up" from hibernate or suspend, then screen stays black.

Any ideas on this issue?

I have the following Kernel Version, dunno if it is important
2.6.35-28-generic

---

### Post by mörgæs on 2011-04-29
Hi, welcome to the fora.

This has been a problem for some time. I don't have any precise answer to you, but you could try a clean install of 11.04 after a month or two, when the release is getting stable.

---

### Post by nihonbun on 2011-04-29
My computer does that as well when I install the fglrx video driver.  If I leave it uninstalled, I have no problems with suspend/wake or hibernate.  I'd disable your proprietary driver for now if I were you, and look for a way to get a video card driver that works (perhaps a different version, but I'm not sure).

---

