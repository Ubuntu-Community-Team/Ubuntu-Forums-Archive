---
title: "HELP.. epsxe wont work.. and the faq doesnt help..."
date: 2007-08-05
forum: Gaming &amp; Leisure
---

### Post by ffobsession on 2007-08-05
[I]* Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
/usr/local/bin/epsxe: line 6:  6423 Segmentation fault      (core dumped) ./epsxe[/I]

and then nothing happens and the screen closes... what am i doing wrong?! >_<

---

### Post by ffobsession on 2007-08-05
```
* Running ePSXe emulator version 1.6.0.
* Memory handlers init.
* ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN].
* Loading ISO Format [BIN/IMG2352] ok
* NTSC cdrom detected.
* Init gpu[0][libgpuPeteXGL2.so.2.0.8]
/usr/local/bin/epsxe: line 6: 6423 Segmentation fault (core dumped) ./epsxe
```

and then nothing happens and the screen closes... what am i doing wrong?! >_<

---

### Post by hikaricore on 2007-08-05
Do not make duplicate threads.

That is all.

---

### Post by acoustibop on 2007-08-06
Personally, I'd say don't bother.  ePSXe is hard work in Linux, and is getting a little old now, as well - there hasn't been a new version for 4 years.

Try [pSX Emulator]("http://psxemulator.gazaxian.com/").  It's still in active development, installation is as easy as installing libgtkglext1 (in the repositories), tarring the pSX file into a folder and adding a Playstation BIOS.  It requires very little configuration, as well.  One of the problems I've had with ePSXe is getting it to work with analog sticks - pSX works with most analog controllers without problems.

---

