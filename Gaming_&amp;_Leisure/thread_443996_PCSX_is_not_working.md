---
title: "PCSX is not working"
date: 2007-05-14
forum: Gaming &amp; Leisure
---

### Post by doom_fan on 2007-05-14
I have recently switched to Linux Ubuntu 7.04 however when I used windows I loved to play the PS1 version of silent hill on my PC though a PS1 emulator.I found a Linux emulator called PCSX but I can't get it working with silent hill.It says it is not a PS1 disc or something like that.Then it boots up but is a very small window and is WAY too fast.Any ideas and does anybody else use PCSX?

---

### Post by acoustibop on 2007-05-15
PCSX is quite an old emulator, doom_fan.  The two Playstation emulators most commonly in use are probably [ePSXe]("http://www.epsxe.com/news.php") and [pSX]("http://psxemulator.gazaxian.com/") - both have Linux ports.

ePSXe is an enhancing emulator, while pSX, which I prefer, concentrates on accuracy.  It's also extremely easy to run in Ubuntu, needing only libgtkglext1 (easily done in Synaptic) on a stock Ubuntu installation.  You simply untar the package somewhere convenient, such as your Home folder, put a Playstation BIOS in the bios subfolder and you're good to go.  You will need to configure your controller, of course, and some configuration will help, particularly increasing latency on the Sound tab but, really, it'll play pretty much 'out of the box.'

ePSXe is, unfortunately, not nearly so straightforward to get running and, for optimum results, you'll need to find the optimum plugins for your system and install and configure them.  I'd only recommend it if you _really_ want an enhanced playing experience.

One of the contributors here, dfreer, has produced an [installer for pSX]("http://ubuntuforums.org/showthread.php?t=394097&highlight=psx"), and also for Ultima's Frontend, an extremely useful adjunct to pSX produced by one of the admins in the [pSX forums]("http://psxemulator.proboards54.com/").

---

### Post by doom_fan on 2007-05-15
> **acoustibop said:**
> PCSX is quite an old emulator, doom_fan.  The two Playstation emulators most commonly in use are probably [ePSXe]("http://www.epsxe.com/news.php") and [pSX]("http://psxemulator.gazaxian.com/") - both have Linux ports.

ePSXe is an enhancing emulator, while pSX, which I prefer, concentrates on accuracy.  It's also extremely easy to run in Ubuntu, needing only libgtkglext1 (easily done in Synaptic) on a stock Ubuntu installation.  You simply untar the package somewhere convenient, such as your Home folder, put a Playstation BIOS in the bios subfolder and you're good to go.  You will need to configure your controller, of course, and some configuration will help, particularly increasing latency on the Sound tab but, really, it'll play pretty much 'out of the box.'

ePSXe is, unfortunately, not nearly so straightforward to get running and, for optimum results, you'll need to find the optimum plugins for your system and install and configure them.  I'd only recommend it if you _really_ want an enhanced playing experience.

One of the contributors here, dfreer, has produced an [installer for pSX]("http://ubuntuforums.org/showthread.php?t=394097&highlight=psx"), and also for Ultima's Frontend, an extremely useful adjunct to pSX produced by one of the admins in the [pSX forums]("http://psxemulator.proboards54.com/").
Thanks a lot I will try to use both because ePSXe is what I used in windows.

---

### Post by acoustibop on 2007-05-15
You're welcome, doom_fan.  But if you haven't tried pSX, then do - I find it the superior emulator both in Windows and Linux.

---

### Post by DoktorSeven on 2007-05-15
Wow, thanks for noting that pSX has a Linux client now.  Awesome.

Oh, and pSX seems to be less compatible with games than ePSXe and a little slower, in my experience, but it's a lot easier to get set up and running... :)

---

### Post by acoustibop on 2007-05-16
I'd say pSX is faster than ePSXe, actually, DoktorSeven.  As to compatibility, it depends very much which games you look at.  Certainly, there are games that ePSXe runs that pSX doesn't (or doesn't run as well), but equally there are games that pSX runs that ePSXe doesn't - or doesn't run as well.

Two things really got me using pSX - the first, was pSX' accuracy as compared to other emulators - it was noticeable that the other emulators were introducing graphical inaccuracies, while pSX portrayed the same images correctly.  I have a PAL Playstation, so there were a number of NTSC games that I'd only ever played in emulators, and I thought some of the inaccuracies were actually correct for the game until pSX demonstrated otherwise!

The other thing thing was my gradual realisation of pSX 'transparency' - that is, there is much less realisation that you are playing a game in an emulator with pSX than with other emulators, and so you get much more immersed in the game.

However, in some ways it's difficult to compare pSX with other Playstation emulators, since the other more-or-less current ones are mainly aimed at enhancing games and choice and configuration of plugins tends to be critical, while pSX is around accurate emulation, includes very little in the way of filtering etc, and is pluginless.  The accuracy is a little disconcerting when you're used to enhancement, but, as I said, once I realised that pSX was rendering images more accurately than the enhancing emulators, that soon wore off.

---

