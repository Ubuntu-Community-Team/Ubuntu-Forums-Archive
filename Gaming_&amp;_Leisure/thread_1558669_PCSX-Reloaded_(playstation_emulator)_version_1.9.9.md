---
title: "PCSX-Reloaded (playstation emulator) version 1.9.92 has been released."
date: 2010-08-22
forum: Gaming &amp; Leisure
---

### Post by thatguruguy on 2010-08-22
I run my emulators on my mythbuntu box.  While pcsx-r typically ran better on that box than pcsx-df did, it was hampered by the fact that it wouldn't properly take a file/rom name as an argument when opening full screen and without a gui, so it couldn't launch directly from mythbuntu.  That problem has been fixed as of the August 5, 2010 release of version 1.9.92, which is available for download here: [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048).  You can download it as either a 32-bit or 64-bit deb.

As noted on the pcsx-r [homepage]("http://pcsxr.codeplex.com/"), pcsx-r is not affiliated with pcsx-df and/or the original pcsx.

As a side note, my old roms of Crash Bandicoot 1, 2 and 3 (which had run poorly for me under other emulators) now run without a hitch.  Try it for yourself, and see if this new release fixes some nagging problems for you, too.

---

### Post by Mike_IronFist on 2010-08-22
Awesome! Thanks for the info!

---

### Post by texaswriter on 2010-08-27
working great

---

### Post by nisisb on 2010-08-28
Look at the article before you entered my misunderstanding, and that your opinion is unique, brilliant! It was wonderful! Thank you for letting me out of the lost.

---

### Post by texaswriter on 2010-08-29
Hrrm, those <insert language here> to <English> translators don't seem to work so great it would seem.

---

### Post by emoguitarist06 on 2010-09-15
Just downloaded an installed on Lucid 64bit and it's running Final Fantasy Tactics pretty good (a little sluggish sometimes) but when I got the first save point it said my memory card was corrupted! What should I do?

Also what would be the best resolution to play this game at? I tried checking the full-screen box and it was super buggy
I have an Asus Eee PC 1201N Netbook, here are my specs
```
**Display**	12.1" LED-backlit WXGA screen (1366 x 768)
**CPU & Chipset**	Intel® Atom™ 330 Dual Core processor
NVIDIA® ION™ Graphics
**Memory**	4GB DDR2 SO-DIMM
```

---

### Post by ShadowTek on 2010-09-15
> **emoguitarist06 said:**
> Just downloaded an installed on Lucid 64bit and it's running Final Fantasy Tactics pretty good (a little sluggish sometimes) but when I got the first save point it said my memory card was corrupted! What should I do?

Also what would be the best resolution to play this game at? I tried checking the full-screen box and it was super buggy
I have an Asus Eee PC 1201N Netbook, here are my specs
```
**Display**    12.1" LED-backlit WXGA screen (1366 x 768)
**CPU & Chipset**    Intel® Atom™ 330 Dual Core processor
NVIDIA® ION™ Graphics
**Memory**    4GB DDR2 SO-DIMM
```

pcsx-r isn't multithreaded, is it? If not, then your just running with 1.6 GHz, which I think might be a little slim for PSX emulation.

Did one of your cores max out while playing?

---

### Post by mister_playboy on 2010-09-16
> **emoguitarist06 said:**
> but when I got the first save point it said my memory card was corrupted! What should I do?

The fake BIOS that comes with the emulator does not handle memory cards correctly.  You'll need to use a real PS BIOS file instead.

Can't discuss that here, of course. :rolleyes:  Ask Google.

---

### Post by thatguruguy on 2010-09-16
> **emoguitarist06 said:**
> Just downloaded an installed on Lucid 64bit and it's running Final Fantasy Tactics pretty good (a little sluggish sometimes) but when I got the first save point it said my memory card was corrupted! What should I do?

Also what would be the best resolution to play this game at? I tried checking the full-screen box and it was super buggy
I have an Asus Eee PC 1201N Netbook, here are my specs
```
**Display**    12.1" LED-backlit WXGA screen (1366 x 768)
**CPU & Chipset**    Intel® Atom™ 330 Dual Core processor
NVIDIA® ION™ Graphics
**Memory**    4GB DDR2 SO-DIMM
```

I'm running pcsx-r on an AMD box (Athlon II dual-core 250) with an nVidia 8400 GS with no problems.  To get it to run full-screen, I set the resolution to my screen resolution (1380x768) and have "Fullscreen" checked in the graphics setup.  I unchecked the box that says "Keep psx aspect ratio".

I had issues with the "memory card" as well, and then one day it started working.  Since I didn't do anything in particular to fix it, I can't really help you on that issue.

---

