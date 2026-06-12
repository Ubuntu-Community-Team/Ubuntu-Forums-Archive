---
title: "Fallout 3 lag (WINE, PlayOnLinux)"
date: 2015-10-17
forum: Gaming &amp; Leisure
---

### Post by righN on 2015-10-17
I installed Fallout 3 and in very start i don't have any problems any  lag. When i needed to complete mission with G.O.A.T answers games starts  lagging. I tried to rename Music folder but don't doesn't help.

---

### Post by mystics on 2015-10-18
Just a few questions:

-What hardware (e.g. CPU, RAM, video card, etc.) do you have? (Please be as specific as possible here!)

-If your computer originally came with Windows and you played it on that, did it run well there?

-Have you tried playing the game past the G.O.A.T. exam? If so, how was the performance?

-Are you playing this through Steam?

---

### Post by righN on 2015-10-19
1. Hardware 

CPU : AMD Sempron Processor 3100+ 1.8 GHz Single-Core (that's sucks)
RAM : 2GB
Video Card : AMD Radeon HD 5450 512 MB
OS : Ubuntu 15.04

2. I don't tried Fallout 3 on Windows :/
3. Yes i tried, everytime i restart the game there's isn't any lag but if i walk a little bit from spawn point games is lagging CPU load was 60-85%
4. No.

---

### Post by mystics on 2015-10-19
Fallout 3's requirements are as follows from their help page: [http://help.bethesda.net/app/answers/detail/a_id/9976/~/what-are-the-minimum-and-recommended-pc-requirements-for-fallout-3%3F](http://help.bethesda.net/app/answers/detail/a_id/9976/~/what-are-the-minimum-and-recommended-pc-requirements-for-fallout-3%3F)

> 
Operating system: Windows XP/Vista 
**Processor: 2.4 Ghz Intel Pentium 4 or equivalent processor **
**Memory: 1 GB (XP)/ 2 GB (Vista)** 
Hard disk space: 7 GB 
Video: Direct X 9.0c compliant video card with 256MB RAM (NVIDIA 6800 or better/ATI X850 or better) 
Sound: DirectX®: 9.0c 
Controller support: Xbox 360 controller 
Supported Video Card Chipsets: 
NVIDIA GeForce 200 series, Geforce 9800 series, Geforce 9600 series, Geforce 8800 series, Geforce 8600 series, Geforce 8500 series, Geforce 8400 series, Geforce 7900 series, Geforce 7800 series, Geforce 7600 series, Geforce 7300 series, GeForce 6800 series
ATI HD 4800 series, HD 4600 series, HD 3800 series, HD 3600 series, HD 3400 series, HD 2900 series, HD 2600 series, HD 2400 series, X1900 series, X1800 series, X1600 series, X1300 series, X850 series.


So you're barely meeting the RAM requirements and your processor is slow. That's not a particularly good combination, especially with Wine/PlayOnLinux also adding on to resource use and general problems (i.e. unless I'm mistaken, Wine doesn't play games quite as well as Windows does). My guess is that Bethesda sets the minimum requirements to the assumption of low settings and a framerate that sticks mostly at or slightly above 30 FPS, so failing to meet them will no doubt cause you to start dropping below that eventually.

In short, I don't think that your computer is capable of running Fallout 3 reliably. You could try Windows if your computer has that, but I doubt it will help much with that RAM and CPU.

---

### Post by righN on 2015-10-19
But Elder Scrolls IV : Oblivion is same reqs. I installed it with using wine, lags but not so much how lags Fallout 3. And i played games on Windows like Assassin's Creed, Mirror's Edge with little lag.

---

### Post by righN on 2015-10-19
I think problem is sound drivers, because when i start the game and always be in spawn point i getting about 17-30fps but when i move and hear more sounds fps drops. I do debug and when fps drop debug shows this error ALSA lib pcm.c:7843:(snd_pcm_recover) underrun occurred

---

### Post by mystics on 2015-10-19
> **righN said:**
> But Elder Scrolls IV : Oblivion is same reqs. I installed it with using wine, lags but not so much how lags Fallout 3.

The *minimum* requirements for Oblivion are a little lower than Fallout 3. As specified by 2K's support site: [http://support.2k.com/hc/en-us/articles/201334233-The-Elder-Scrolls-IV-Oblivion-PC-System-Requirements](http://support.2k.com/hc/en-us/articles/201334233-The-Elder-Scrolls-IV-Oblivion-PC-System-Requirements)

> 
Windows XP, Windows 2000, Windows XP 64-bit 
[B]512MB System RAM 
2 Ghz Intel Pentium 4 or equivalent processor [/B]
128MB Direct3D compatible video card and DirectX 9.0 compatible driver; 
8x DVD-ROM drive 
4.6 GB free hard disk space 
DirectX 9.0c (included) 
DirectX 8.1 compatible sound card 
Keyboard, Mouse


Those aren't the same as Fallout 3. Furthermore, your RAM is well over the minimum required (rather than barely passing), and your processor is quite a bit closer to passing. That's a considerable difference.

> And i played games on Windows like Assassin's Creed, Mirror's Edge with little lag.

For starters, you were playing them on Windows, where they were designed to be played. Wine can help us play some Windows games, but they won't offer a 1:1 experience except in very rare cases. There are likely to be performance issues that may not necessarily be caught by someone reviewing the game on the AppDB because their computer is powerful enough to overcome that. Computer straddling the line may not work. I have the same problem with The Witcher.

Beyond that, there's also optimization and stability to consider, and Fallout 3 is hardly a good example of how to do either. I remember Assassin's Creed doing well in that regard. Never played Mirror's Edge on PC.

That said, it's a little odd that Assassin's Creed and Mirror's Edge were running much better than Fallout 3. By any chance, were you keeping track of framerates to know what the actual numbers were?

---

### Post by righN on 2015-10-20
> **mystics said:**
> The *minimum* requirements for Oblivion are a little lower than Fallout 3. As specified by 2K's support site: [http://support.2k.com/hc/en-us/articles/201334233-The-Elder-Scrolls-IV-Oblivion-PC-System-Requirements](http://support.2k.com/hc/en-us/articles/201334233-The-Elder-Scrolls-IV-Oblivion-PC-System-Requirements)



Those aren't the same as Fallout 3. Furthermore, your RAM is well over the minimum required (rather than barely passing), and your processor is quite a bit closer to passing. That's a considerable difference.



For starters, you were playing them on Windows, where they were designed to be played. Wine can help us play some Windows games, but they won't offer a 1:1 experience except in very rare cases. There are likely to be performance issues that may not necessarily be caught by someone reviewing the game on the AppDB because their computer is powerful enough to overcome that. Computer straddling the line may not work. I have the same problem with The Witcher.

Beyond that, there's also optimization and stability to consider, and Fallout 3 is hardly a good example of how to do either. I remember Assassin's Creed doing well in that regard. Never played Mirror's Edge on PC.

That said, it's a little odd that Assassin's Creed and Mirror's Edge were running much better than Fallout 3. By any chance, were you keeping track of framerates to know what the actual numbers were?

I just run game from PlayOnLinux. Choose game then click Configure in debug flags write fps and then close Configure window and click Debug. Play a little bit then you can close game and .log file will show up where's FPS.

---

