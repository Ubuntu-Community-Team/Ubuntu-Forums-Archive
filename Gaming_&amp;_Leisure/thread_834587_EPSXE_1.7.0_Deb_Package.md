---
title: "EPSXE 1.7.0 Deb Package"
date: 2008-06-19
forum: Gaming &amp; Leisure
---

### Post by phildaman46 on 2008-06-19
Is there anywhere I can get Epsxe as a deb package? Possibly for the 64bit version of Ubuntu 8.04 so it would be easier to install and run. If not, I will use the Windows version with Wine instead. But I prefer a native Linux port if its possible.

Edit: Oops, there is no Epsxe 1.7.0 for Linux. How about Epsxe 1.6.0 instead?

---

### Post by phildaman46 on 2008-06-19
I guess its better to just run Epsxe under Wine uh? Thats the easiest way to get it to work.

---

### Post by Vadi on 2008-06-19
You can always ask getdeb.net to make a .deb, if it's a freely-distributable program.

---

### Post by acoustibop on 2008-06-20
There is no Linux version of ePSXe (or source) available as yet - it may be a long time.

Personally, I'd recommend using a more up-to-date, better and much easier to use Playstation emulator - [pSX Emulator]("http://psxemulator.gazaxian.com/").

---

### Post by fieldstone on 2008-06-24
> **acoustibop said:**
> There is no Linux version of ePSXe (or source) available as yet - it may be a long time.

Personally, I'd recommend using a more up-to-date, better and much easier to use Playstation emulator - [pSX Emulator]("http://psxemulator.gazaxian.com/").

There definitely is a Linux version of ePSXe 1.6.0, and there has been for years. And at least for me, it works far better than pSX.

---

### Post by acoustibop on 2008-06-24
> **fieldstone said:**
> There definitely is a Linux version of ePSXe 1.6.0, and there has been for years. And at least for me, it works far better than pSX.

Sorry, I meant Linux version of ePSXe 1.7.0, fieldstone.

But I'd have to take issue with you over comparisons between pSX and ePSXe.  Even in Windows, pSX beats the pants off ePSXE; in Linux, where setting up ePSXe and configuring it is such a headache; it's definitely no competition.  And I'm speaking as someone who used ePSXe quite happily for 6 years or more before pSX came along.  Even the first release of pSX was enough to show me just what ePSXe didn't do that it should.

pSX has better compatibility, runs with no slowdowns on even quite moderately specced machines, presents such an accurate picture (I never realised how badly ePSXe's enhancement distorts the picture until I tried pSX), is so easy to install and configure - where do I stop?

The irony of it is that, while pSX runs better than ePSXe in Windows, pSX runs better in Linux than its Windows version - while ePSXe runs nothing like as well as in Windows.

Additionally, one of the few points that ePSXe can score over pSX in Windows, that you can toggle between digital and analog control by pressing F5, while in pSX you have to do it in configuration, is missing in Linux.  In fact, you can't even change between digital and analog control without stopping the emulator and restarting it with a different switch in ePSXe.  In pSX, it's exactly the same as Windows - which means you can change controller assignment ingame, even though it's fiddly.

---

### Post by DoktorSeven on 2008-06-24
1) The answer to the question is that it's probably fairly difficult to get a proper debian package made for ePSXe.  That said, it's just as easy to grab ePSXe and put it in its own directory in your home directory, then make a launcher script that does something like:

```

#!/bin/bash
cd ~/epsxe
./epsxe

```

...then make it executable (toggle the executable flags on the file) and make a link to it from your menu or desktop to run it.  Not everything needs a debian package.

2) I do agree with fieldstone that ePSXe is still a great emu.  I get slowdowns, skipping, and other issues with pSX, not to mention that several games have annoying bugs (Castlevania: SotN has LONG pauses occasionally, for example) and worse, I can't see the edges of the screen in fullscreen mode as they've been chopped off (yes, everything's properly configured; no, it doesn't happen on any other fullscreen game/emulator/program); there are a few others on pSX's forum that have the same issue and it has so far been unresolved.

So blanket statements that pSX is better than ePSXe in all cases is incorrect.  I'm not putting down pSX at all -- on the contrary, it's a nice emulator that is more user-friendly for those who don't want to do all the plugin work it takes to get ePSXe working (which I also like because it's more in line with the Linux way of doing things -- different choices for different configurations), and I applaud their efforts.  Just know that for some people, ePSXe works much better.

---

### Post by acoustibop on 2008-06-24
> **DoktorSeven said:**
> ... So blanket statements that pSX is better than ePSXe in all cases is incorrect... 
Obviously, it's incorrect, DoktorSeven, and it's not what I said.  I even pointed out one aspect (admittedly small, and only in Windows) where ePSXe does something better than pSX.  But as you yourself agree, most people find pSX to be a better Playstation emulator than ePSXe.
> ... Just know that for some people, ePSXe works much better.
I'm quite aware of that; as you know: we've discussed this before, and I have considerably more respect for your opinions on this than many ePSXe 'fanboys' (which is not to suggest that you're a 'fanboy!'  However, I have to reiterate that, across the board, pSX does far better than ePSXe.
> ... because it's more in line with the Linux way of doing things -- different choices for different configurations... 
I have to dispute this.  The Linux way of doing things is that you can change things as you want *because you have access to the source*.  Neither emulator scores in this respect, as the source of neither emulator is freely available.

---

### Post by NightCrawler03X on 2008-06-27
*warning: shameless plug below*

I hear people say that epsxe is "hard" to install on a GNU/Linux system, well a while ago I wrote an install script that automatically downloads epsxe and it's plugins and puts it all in the right place. I posted this installer to a thread in this forum:

[http://ubuntuforums.org/showthread.php?t=550304](http://ubuntuforums.org/showthread.php?t=550304)

You still have to setup the plugins, but that part is easy (my installer just makes sure everything is put in the correct folders and whatnot).
And you'll still have to find a bios image, but that isn't too hard either.

---

### Post by phildaman46 on 2008-07-06
> **NightCrawler03X said:**
> *warning: shameless plug below*

I hear people say that epsxe is "hard" to install on a GNU/Linux system, well a while ago I wrote an install script that automatically downloads epsxe and it's plugins and puts it all in the right place. I posted this installer to a thread in this forum:

[http://ubuntuforums.org/showthread.php?t=550304](http://ubuntuforums.org/showthread.php?t=550304)

You still have to setup the plugins, but that part is easy (my installer just makes sure everything is put in the correct folders and whatnot).
And you'll still have to find a bios image, but that isn't too hard either.

Can you compile a deb package for 32bit and 64bit?

---

### Post by NightCrawler03X on 2008-07-06
I don't need to compile a deb package for either 64-bit or 32-bit.
All my installer does is download all of the required plugins, and epsxe itself, before sorting everything into the right folders.

If you're running a 32-bit OS, just make sure you have all the required libraries, and likewise if you're running a 64-bit OS, make sure you have all the required 32-bit libraries. Do this and ePSXe should run just fine.

---

### Post by ringmaster on 2008-11-20
The easy way is to use wine, [here is a tutorial]("http://miqueridopinwino.blogspot.com/2008/11/tutorial-utilizando-el-emulador-epsxe.html") with a pre-configured version of 1.7.0, you only need to install wine (sudo apt-get install wine) and run it (after downloading BIOS, of course, you must have a real playstation).

It is in Spanish, and after trying pSX emulator and ePSXe, ePSXe is far better than pSX, without headaches with Pulseaudio, and with a adecuate config it is like the PS but with more resolution, which is more than welcome.

The linux version of ePSXe is buggy (freezes, dependency hell, etc), but this way it works very well.

Hope it helps those with problems running a good PS emulator on linux. The manual is in spanish but you can translate it with google translator (to the right-up). Excuse me for my english.

---

