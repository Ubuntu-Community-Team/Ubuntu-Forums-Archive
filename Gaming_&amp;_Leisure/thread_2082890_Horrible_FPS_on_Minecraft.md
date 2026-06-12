---
title: "Horrible FPS on Minecraft"
date: 2012-11-10
forum: Gaming &amp; Leisure
---

### Post by JamesTheAwesomeDude on 2012-11-10
I tried to play Minecraft (a Java game) on Ubuntu, and the FPS was horrible. (This was a total surprise; I'd expected Java to do much better on Linux. Same results, no matter which JRE I was using.) I was only getting around 2 FPS, even when the same machine got 24-ish FPS on Windows. (I'm running a dual-boot, by the way.)
I have a decent graphics card, a Radeon HD 4350, and I run it at 1024X1280 on both OS's.

My computer is 64-bit, but the guy that we got it from didn't know that, so it had a 32-bit Windows on it. This led us to believe that the computer was 32-bit for quite a while. Eventually, we discovered the extra power, and promptly reinstalled Ubuntu with the 64-bit version. Minecraft's FPS nearly doubled: Still unplayable.
The Radeon HD 4350 is [supposed to have good 3D acceleration]("https://help.ubuntu.com/community/RadeonDriver"), but I'm not buying it when I get 3 FPS with a 64-bit system and 3 Gig of RAM.

I was wondering whether it would be worth it to use the proprietary AMD Calalyst driver, or am I just doing something terribly wrong with the current one?

---

### Post by efflandt on 2012-11-11
Although I am not familiar with that specific video card, if **Additional Drivers** does not show you having **flgrx** "activated and in use", try activating flgrx and see if that helps.

What cpu do you have?

Minecraft is playable with keyboard and wireless mouse on my 1 GHz 2 core 2 GB tablet PC with Radeon HD 6250 graphics in 64-bit 11.10 or 12.04 w/openjdk-6 booted from SD card.  Admittedly minecraft 1.4.2 only averages around 10-20 fps, but that is not so noticeable on its small 10" 1280x800 screen that I normally only use when out of town.

There are some video options in minecraft for Fast vs. Fancy graphics, Fast vs. Balanced, reduced particles, etc.  While they have been trying to optimize minecraft speed, some things added in 1.4.2 make it potentially slower than 1.3.2 on a slow computer (not noticeable on much faster desktop).

---

### Post by mzrk7 on 2012-11-11
I would try to use the proprietary drivers. The newest drivers won't work anymore with your card, so you'll have to look for legacy drivers. Good luck :)

---

### Post by JamesTheAwesomeDude on 2012-11-24
Well, darn.

When I upgraded to 12.10, the Proprietary Drivers option was nowhere to be found. (The download from AMD's site is... horrible. My God, that will screw up your system SOOOOOO badly. I will NEVER, EVER use that ever again. I actually had to reinstall Ubuntu, after using the Root Shell in Safe Mode to back up my files.)

NOTE: the FGLRX driver, available through the Proprietary Drivers option, did not screw up my system at all, but it only gave me about a 1 FPS boost.
The Xorg-edgers' drivers helped a little, getting me up to about 4 FPS, but it was still not very playable.

---

### Post by mentorious on 2012-11-24
I've installed Catalyst 12.11 beta8 manually and works really good :)

16-20fps in Minecraft with GLSL shaders + Sonic unbelieve pack.

---

### Post by holastickboy on 2012-11-25
> **JamesTheAwesomeDude said:**
> Well, darn.

When I upgraded to 12.10, the Proprietary Drivers option was nowhere to be found. (The download from AMD's site is... horrible. My God, that will screw up your system SOOOOOO badly. I will NEVER, EVER use that ever again. I actually had to reinstall Ubuntu, after using the Root Shell in Safe Mode to back up my files.)

NOTE: the FGLRX driver, available through the Proprietary Drivers option, did not screw up my system at all, but it only gave me about a 1 FPS boost.
The Xorg-edgers' drivers helped a little, getting me up to about 4 FPS, but it was still not very playable.

I've had nothing but issues with drivers and 12.10, especially because they removed Jockey, which was the program that prompted you to install the additional drivers previously. I would recommend you install 12.04 if you are still having issues, that's what fixed my problems! 12.04 is a LTS release too, so you're not being left behind, even though it's technically an older release!

---

### Post by mastablasta on 2012-11-27
> **JamesTheAwesomeDude said:**
> Well, darn.
 
When I upgraded to 12.10, the Proprietary Drivers option was nowhere to be found. (The download from AMD's site is... horrible. My God, that will screw up your system SOOOOOO badly. I will NEVER, EVER use that ever again. I actually had to reinstall Ubuntu, after using the Root Shell in Safe Mode to back up my files.)
 
NOTE: the FGLRX driver, available through the Proprietary Drivers option, did not screw up my system at all, but it only gave me about a 1 FPS boost.
The Xorg-edgers' drivers helped a little, getting me up to about 4 FPS, but it was still not very playable.
 
 
the card is not supported by AMD proprietary drivers anymore in 12.10. ATI dropped support for HD3000 and hd 4000 series. you need to install legacy drivers and downgrade the X (safest via PPA) or simply use 12.04 and install the drivers from jockey (additional drivers interface). 12.04 is supported for 5 years anyway by that time opensource drivers for this card will get even beter and you might not be playing minecraft anymore anyway... :P

---

### Post by JamesTheAwesomeDude on 2012-11-27
> **mastablasta said:**
> The card is not supported by AMD proprietary drivers anymore in 12.10. ATI dropped support for HD 3000 and HD 4000 series. you need to install legacy drivers and downgrade the X (safest via PPA) or simply use 12.04 and install the drivers from jockey (additional drivers interface). 12.04 is supported for 5 years anyway by that time open-source drivers for this card will get even better and you might not be playing Minecraft anymore anyway... :P
Hmm... I'm actually hoping not to have to downgrade to 12.04, but what's this about the legacy drivers? I've heard that name somewhere, but I can't quite place it...
The Jockey interface is actually missing from my Ubuntu 12.10; should I just do [FONT=Courier New]sudo apt-get install jockey[/FONT]?

P.S., I'm gonna play Minecraft till I DIE, so I really need some good drivers for my precious Ubuntu! :) (Windows won't work in VirtualBox; says it needs to be re-activated or something like that...)

---

### Post by mastablasta on 2012-11-28
jockey is replaced by some other drivers thing... [http://www.omgubuntu.co.uk/2012/07/ubuntu-12-10-alpha-3-released](http://www.omgubuntu.co.uk/2012/07/ubuntu-12-10-alpha-3-released) right in the sources menu.
 
legacy drivers will downgrade the X and some other thing. there is a PPA for them: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
 
if you are using Ubuntu with unity the unity could be the culprint. you should check the porcesses that hog down minecraft.
 
i think KDE would auto disable special effects (or is it an option) when you run full screen applicaiton such as games

---

### Post by holastickboy on 2012-11-28
It's an option, very easy though, just a matter of unticking a box. Not home to find it at the moment, otherwise I would point where it was. I think it was in appearance though

---

### Post by JamesTheAwesomeDude on 2012-12-29
Okay, I decided to go back to 12.04.

Something screwed up with Jockey, it says that "Ubuntu has encountered an internal error" whenever I try to open the Additional Drivers.

[FONT="Courier New"]sudo aptitude install fglrx[/FONT] didn't make my computer explode, but it didn't improve my MC framerate.

The error occurs in both OpenJDK, and the Sun JRE (which is officially suggested by the Minecraft website.)

When running Minecraft via the terminal, I get a TON of "WARNING: Can't keep up! Did the system time change, or is the server overloaded?" messages, even though the system time DIDN'T change, and the computer is most definitely NOT overloaded.

---

