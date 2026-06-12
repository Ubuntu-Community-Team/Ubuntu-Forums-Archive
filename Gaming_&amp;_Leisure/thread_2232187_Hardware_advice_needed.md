---
title: "Hardware advice needed"
date: 2014-06-30
forum: Gaming &amp; Leisure
---

### Post by TPJ on 2014-06-30
I'm going to buy some new hardware, which will be used also for gaming, and I need some advice.

My situation:
  * I have a powerful home server (Intel i3 3.30GHz, 8 GB RAM, PCI Ex 2.0, power supplier 500W).
  * I'm going to buy a low-budget laptop with nVidia 720GT.

The home server will be used for:
  * files storage (music, movies, backups),
  * movies ripping and encoding,
  * building software (compilation),
  * games (both Windows and Linux - Ubuntu).

The laptop will be used for:
  * working (browsing internet, editing text files),
  * occasionally watching movies,
  * occasionally gaming.

Target systems:
  * Ubuntu LTS (right now, 14.04)
  * Windows 7 (for some games which don't run on Linux)

The games:
  * Europa Universalis 3, EU4, Crusader Kings 2, Silent Hunter 3/4/5 (the 1st part can be played on DOSBox), Truck simulators, perhaps the Tropico series.
  * Don't mind playing with PlayOnLinux, also developing my own scripts.

Graphics cards I'm thinking about (for the home server):
  * nVidia GT 630
  * nVidia GT 740
(Right now the built-in Intel graphics chip is used, which is enough for working.)

Now, my thoughts:

Why nVidia: because, AFAIK, nVidia works better on Linux. But my knowledge might be a couple of years (5+) old.

Why 630:
  * because it's cheaper,
  * I think it's enough to run the games I'm interested in,

Why 740:
  * because it's much better,
  * because it would be fine for the home server to have better graphics card than the laptop


What do you think?

Am I right that nVidia is a better choice than ATI?
Which graphics card should I buy for the home server?
Is Windows 7 better choice for games (including the older ones) than Windows 8? (I haven't been using Windows for years...)

---

### Post by oldrocker99 on 2014-06-30
The GeForce 750ti is ~$150, is twice as fast as my 650ti (according to Phoronix' tests) at about the same price, and uses HALF the power. If you can afford it, I'd go with that.

While ATI is preferred by many Windows gamers for allegedly superior hardware, ATI's Linux drivers have been notoriously awful for the six years I've been using Linux. nVidia's drivers aren't perfect (PhysX is present, but uses the CPU, not the GPU as it does for Windows), but they're way, way better than ATI's. 

As far as using Windows, yes, 7 is better than 8 (and the sun rises in the east), but I just deleted my Windows partition because every time I booted into Windows 7, I got majorly annoyed at that porous, vulnerable, do-things-the-way-WE-say-to-do-them OS, and, by now, there are some very good AAA Linux titles from Steam that I want to play, so why risk contracting malware to play a game? All the games you mentioned above (except for Silent Hunter) are natively available on Steam for Linux.

---

### Post by efflandt on 2014-07-04
When I bought a gaming laptop last October (which has combo Intel and Nvidia GTX 765M), I specifically got it with Win7 while I could, so I would not have to deal with Win8 UFEI and secure boot. And although it uses regular msdos partitions, something is peculiar about its MSI BIOS or mbr because when I wanted to leave the standard mbr and put grub on sda4, something kept changing the boot flag back to sda2. So I put grub in the mbr of a USB memory stick and use that to boot into Linux, which I guess is sort of a safety feature because few people would even know Linux was on the drive without the USB stick. Eventually I want to switch Linux to a solid state mSata drive (the laptop has places for 2 of those).

Can't help you too much as far as current graphics, except that I have never had any trouble with nvidia graphics with Linux Steam games, etc. like some people with ATI graphics have. Steam chose nvidia for their Linux based Steam OS and hardware. My desktop has an older GTX 550 Ti that works fine for the games I play. I was playing some Steam games like Team Fortress 2 for awhile, but lately have gotten back into minecraft Tekkit mod. My only computer with modern ATI graphics is a 1 GHz 2 core 2 GB tablet PC w/HD 6250 graphics which can barely play minecraft and with 32 GB SSD (Win7 Pro) or SD (Linux) does not have room for Steam games

---

