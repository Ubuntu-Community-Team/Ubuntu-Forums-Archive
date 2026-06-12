---
title: "New user looking for some general help"
date: 2006-01-25
forum: Gaming &amp; Leisure
---

### Post by Raymond_MacEachern on 2006-01-25
Hello all.
I'm currently on a IMac G3 (600 MHz, 512 Ram, 40 gig Hdd) and am running (K)ubuntu and have some other computer around the household that I want to convert to Linux.
It took me a little bit of work to get (K)ubuntu up and running well on the mac and I wanted to know if it will be worth it to convert my other computers to Linux.
The system I am worried about has the following hardware:
AMD Athlon 64 X2 3800+ (2.0GHz Dual Core) CPU
ASUS AX800XL RADEON  X800 XL 256MB PCI-E video card
DFI LANParty UT NF4 ULTRA-D Mobo
1GB  OCZ DDR400 CL2-3-2-6 Ram

Will I be able to game with the 64bit (K)ubuntu disto? I have been looking though the forums and have read posts that say wine will work and then read others that say it will not. Will it work for games?
Also I have read about Cedega which sounds like the best bet for gaming. Will I be able to use Cedega with said disto?
I would also like to know if anyone knows how well a video card such as mine will preform, or even if I would be better off going with the non 64bit install perhaps?
Games I'm looking to play with my system are games such as City of Villians, World of Warcraft, Counter Strike Source, BattleField 2, and Guild Wars.
I'm looking forward to gaming in the open source world of linux via (K)ubuntu. :D

---

### Post by RAOF on 2006-01-25
[QUOTE=Raymond_MacEachern]Hello all.
I'm currently on a IMac G3 (600 MHz, 512 Ram, 40 gig Hdd) and am running (K)ubuntu and have some other computer around the household that I want to convert to Linux.
It took me a little bit of work to get (K)ubuntu up and running well on the mac and I wanted to know if it will be worth it to convert my other computers to Linux.
The system I am worried about has the following hardware:
AMD Athlon 64 X2 3800+ (2.0GHz Dual Core) CPU
ASUS AX800XL RADEON  X800 XL 256MB PCI-E video card
DFI LANParty UT NF4 ULTRA-D Mobo
1GB  OCZ DDR400 CL2-3-2-6 Ram

Will I be able to game with the 64bit (K)ubuntu disto? I have been looking though the forums and have read posts that say wine will work and then read others that say it will not. Will it work for games?
Also I have read about Cedega which sounds like the best bet for gaming. Will I be able to use Cedega with said disto?
I would also like to know if anyone knows how well a video card such as mine will preform, or even if I would be better off going with the non 64bit install perhaps?
Games I'm looking to play with my system are games such as City of Villians, World of Warcraft, Counter Strike Source, BattleField 2, and Guild Wars.
I'm looking forward to gaming in the open source world of linux via (K)ubuntu. :D[/QUOTE]
It depends on how interested you are in fiddling around.  Wine on x86_64 is an exercise in frustration - it works, kinda - and if you've got a primary interest in gaming, wine's going to be 32bit whatever Ubuntu you use.  Just install the i386 version, and you can apt-get wine, use the WineCVS script, whatever, to your heart's content.

Edit: On the other hand, you've got a dual-core processor.  And I don't think you'll be able to use both cores **without** the amd64-smp kernel.  I'm not sure, however - I've never tried.  Maybe one of the x86-smp kernels will also work.

Also, ATI X800s are apparently no end of trouble in Breezy64

---

### Post by Raymond_MacEachern on 2006-01-25
Sad to hear that my video card is nothing but a world of trouble in Linux. I was hoping to finally make a change over to it :/
Anyone else have some input for me?

---

### Post by Perfect Storm on 2006-01-25
You might change to i386(x86) ubuntu if you want to game, to much trouble getting the 64 bits version to be a decent game machine at the moment (so I've heard).

---

