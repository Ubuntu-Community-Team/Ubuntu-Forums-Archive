---
title: "No linux distro is stable on my rig!"
date: 2006-09-15
forum: Desktop Environments
---

### Post by stiz on 2006-09-15
Motherboard: Soyo SY-P4I875P DRAGON 2 v1.0 Black Label
Drives: 250GB & 160GB Maxtor's hooked up to the Intel IDE master port Master/Slave
Video: Saphire ATI Radeon 9500 (NOT pro)
Audio: Chaintech VIA Envy based chipset pci sound card
other: zippy 500w psu, one liteon cdrom & optorite DVDRW attached to the slave Intel IDE port Master/Slave, basic keyboard, logitech mx500 mouse attached standard mouse port..

I had this exact configuration besides the motherboard in a dell sc400 with 875p chipset.  Now that its switched over into a new case with the soyo motherboard no linux distro is stable.  Mouse stops moving after 30sec - 5min of usage.  Windows XP runs fine 24/7.  

The motherboards bios is the newest version set to 'optimized performance defauls' except onboard audio is disabled.  I tried disabling other things in bios I dont need like firewire and ali raid chipset and it made no difference so I set it back to default.  I tried booting acpi=off and no difference.  This system is not stable in the newest OpenSuse distro and Ubuntu and I tried a handfull of other distros in the past and non of them were either.

I am guessing its the motherboard since the same setup was used in my dell with zero problems with linux, rock solid.  Can I boot into live and before the system locks up get some sort of system log to post in this forum to help with diagnostics?

Thank You!

---

### Post by Odinist on 2006-09-15
When the mouse locks up, does the whole system lock? Like, to the point where CTRL+ALT+Backspace doesn't do anything?

---

### Post by evillawngnome on 2006-09-15
Run memtest86, preferably overnight.
Make sure your cpu/ram speed settings are correct.
Make sure your heat sink/fan is mounted properly.
Bad CPU's and RAM are a BITCH to track down. Get this out of the way to eliminate it.

---

### Post by stiz on 2006-09-15
The whole system locks up.  Ill try CTRL+ALT+Backspace.  But I tab nothing moves, ctrl+alt+del nothing, processes that were running on the screen stop (at least visually I know). I end up holding down the power button and powering off.

---

### Post by Odinist on 2006-09-15
I've had that happen to me three different times over that last few years.

Every single time, it's been a video card going out.

Throw a different vid card in there (if you have one lying around). You'll probably have to reconfigure your x-server if the card's of a different chipset than what you had.

There's a good change that'll fix your problem.

---

### Post by evillawngnome on 2006-09-15
Is this an amd processor?
I have a problem with my server at home locking up after any serious uptime. After searching and searching, the only "fix" i found was to have cron reboot the machine every day to keep it sane. :-(

---

### Post by stiz on 2006-09-15
I ran memtest for a few hours, I will try longer.  Its 2-512mb sticks of Crucial PC-3200 running in dual channel mode.  Tends to be pretty stable memory short of getting ECC sticks.  I will try memtest longer.  Runs XP for weeks on end 24/7 and only need to reboot because of updates or software that I just installed.

---

### Post by stiz on 2006-09-15
Sorry left out processor.... It is a P4 2.8ghz Northwood

---

### Post by evillawngnome on 2006-09-15
You know, im going to have to concur with DruidicWisdom about the video card. I've long suspected this is the problem in my AMD machine. Swap it out for something else, maybe a bargain from newegg or tigerdirect and see if that gets you anywhere.

---

### Post by stiz on 2006-09-15
Well one weird thing about the videocard is it is detected as a 9500 pro when its just a plain 9500.  But it goes back to the fact that videocard ran just fine and rock solid in my dell 400sc with ubuntu and other linux distros.  

The only things that have changed from my Dell is a much larger (better) psu, better copper heatsink, a non dell case (odiously), and a totally different motherboard (soyo). I will run memtest tonight for 12+hrs.  

If for some reason I can narrow it down to the videocard for sure.. then I will spend the money for a new one.  I am just not at that point yet to ditch a card I paid $125 for(+$ aftermarket heatsink) that works 100% fine playing games, watching dvds, etc.. on WinXP.  

Thanks for the help allready folks! :D

---

### Post by brucevangeorge on 2006-09-15
What about the motherboard? Maybe that's the problem? Isn't it one of those cheap chinese knockoffs that you can get for about $20?

---

### Post by stiz on 2006-09-15
Actually it was one of the most expensive socket 478 motherboards at the time of purchase $200+  [http://www.soyousa.com/products/proddesc.php?id=287]("http://www.soyousa.com/products/proddesc.php?id=287")

But that 2 me would seem the most logical problem, the motherboard.  Now why that is, is beyond me.  I highly doubt its a hardware malfunction since it has been running 24/7 filesharing for over 2yrs now under windows xp.  

The whole reason I stopped using linux was because of these problems but at the time I never seeked technical support and just went back to windows.  I would really like to get back into the linux game.  I was given an old computer for my girlfriend and I put ubuntu on it, it has REALLY improved since running it 2+yrs ago. I have got the itch to get back to linux bad.

---

### Post by stiz on 2006-09-16
Memtest ran fine overnight, no errors.

---

### Post by Odinist on 2006-09-16
In that case, I say try a vid card... Get a loner from a friend or something first, just to test the theory, and if that fixes the problem, then drop the money on a new one.

---

### Post by mgmiller on 2006-09-16
One other thing to try, in your BIOS, try disabling legacy USB support.

---

### Post by stiz on 2006-09-16
Well good news, 2hrs on Ubuntu 6.10 edgy eft and no such problems (crossing fingers).

---

### Post by stiz on 2006-09-19
Problem solved on Dapper Drake 6.06..

instalation of official ati.com drivers fixed all stability issues.  Seems the newest opensource driver was causing the stability problems in every linux distro I tried with my Saphire Radeon 9500 (non pro)

I am having some questions/issues with aticonfig though.  I started a thread here [http://www.ubuntuforums.org/showthread.php?t=261106]("http://www.ubuntuforums.org/showthread.php?t=261106")

Thank You Ubuntu friends!

---

### Post by Odinist on 2006-09-19
Told ya it was something to do with the vid card. ^_^


Congrats on gettin' her up and runnin!

---

