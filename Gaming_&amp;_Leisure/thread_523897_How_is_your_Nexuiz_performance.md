---
title: "How is your Nexuiz performance?"
date: 2007-08-12
forum: Gaming &amp; Leisure
---

### Post by voided3 on 2007-08-12
Hello, i've noticed on just about any machine I use that nexuiz goes between quite smooth while walking around the map at 60-100+ fps to 10-35fps while there are bots in the room. This goes for everything i've used it on which includes:

-800mhz PIII w/ 512mb ram and a 64mb MX440 on xubuntu 7.04
-Athlon XP-M 1800+ w/ 1.0 GB and a Radeon 9250 256mb on ubuntu 7.04 and winXP
-Athlon XP 2500+ w/ 1.5 GB and a Radeon x1300pro 256mb on ubuntu 7.04 and winXP
-Macbook Pro 2.16 Core Duo, 2GB of ram, x1600 w/ 256mb and OSX

Yes, even on the macbook pro it takes a dip while fighting to about 25 fps when there are other bots around, and on the two machines I listed with windows, it does the same there as it does in ubuntu, even on the lowest of low setting there still is a significant dip. Has anyone else noticed this and is there a way to circumvent it since the game is quite fun?

---

### Post by shynko on 2007-08-12
the reason it does this is sense when there are bots in the room not only does it have some more polygons and such  to display but it has to  run the bots ai.
the only real advice I could give you is to use openbox  here is a how to I found on installing it
[http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox](http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox)

---

### Post by Sockerdrickan on 2007-08-12
I have lame performance for my specs, it is based on quake 1 though so I'm not surprised.

---

### Post by cody50 on 2007-08-12
i've noticed that it slows down considerably with lots of bots and things flying round. even on a decent system.

---

### Post by voided3 on 2007-08-12
shynko, out of curiosity, how can a different window manager help my game performance? I know that beryl/compiz can make 3D drag, but I use either GNOME or XFCE (and as listed, I have used Nexuiz on both WinXP and OSX with similar results). The system I use most for games is the 2500+ setup I have listed, and that has 1.5 GB of ram, so it definitely isn't a matter of free ram, and I have the proprietary driver for the x1300pro installed through the restricted driver manager.  

It may make it look less refined, but the setting I found that makes it the smoothest on that setup when booted into Ubuntu is to have all effects turned off, running at medium quality, 32-bit color, and a 1440x900 resolution (I have a 19" widescreen LCD). I know lowering the res helps too, but it would look horrendous if I did or be too small if I run it windowed.

---

### Post by voided3 on 2007-08-12
For an experiment, I put Nexuiz (2.2.3 instead of the latest 2.3 because I had some problems with it, and it's the same version I have on Ubuntu from the repositories) on WinXP on that same 2500+ setup and ran significantly faster, so my guess is the default answer for ATI Linux users as to why performance isn't where it should be: the drivers. It still took an fps dip when fighting multiple bots, but it would dip to 45-50 instead of 25-35, and at higher settings (still 1440x900, but at "good" quality w/ gloss and open GL shaders on). Unless ATI gets better Linux drivers, I might have to go with nvidia for my next computer build. Strange though because I have used Nexuiz on winXP on the aforementioned computer with a 9250 and 1800+ and it performed the same on both OSes... go figure.

---

### Post by shynko on 2007-08-12
I get better fps on tremulous with openbox  rather than gnome so I was just wondering if it would help you too

---

### Post by buttons on 2007-08-12
Since I upgraded to 2.3 and started using the GLX executable rather than the SDL one, I've not dropped below 200 fps regardless of the action.  I have a few effects turned off, but not 180 fps worth, to be sure.

7800GT, athlon 3800+, 1 GB ram.

EDIT: Though I must say there's a super annoying bug with xfwm4 and nexuiz, where regardless of settings you can see the desktop windows very faintly while in game.  No other game does that.

---

### Post by MaximB on 2007-08-13
the earlier version of Nexuiz worked great with my ATO 9800 Pro videocard under Linux.
but they changed something and not it become unplayable.
similar thing happened with Regnum online, in the beta it worked great with my videocard, but now I can only play in safe mode.

---

### Post by xplinux557 on 2009-08-03
Hi

Nexuiz is usable on my laptop running Hardy, but every once in a while it
makes X crash randomly and Ctrl-Alt-Backspace doesn't work. This usually happens
on the SDL version. But still, when my computer doesn't lock up, I get around 20-40 fps
at the Normal preset and pretty decent graphics.

My laptop's specs:
Intel 965 GMA Chipset
4 GB RAM
Intel Pentium Dual-Core Processor

This game is so addicting and fun, but it doesn't run all that good on my lappy.
I nearly drove myself mad searching Alientrap's website, Launchpad, the Ubuntu
Forums, and other sites for ways to increase Nexuiz's performance without
sacrificing too much eyecandy. :)

---

### Post by hhh on 2009-08-03
Why are you resurrecting a two year old thread? Start a new one. Damn, this forum needs some moderators.

---

### Post by Crunchy the Headcrab on 2009-08-04
> **hhh said:**
> Why are you resurrecting a two year old thread? Start a new one. Damn, this forum needs some moderators.  :?
He probably searched for Nexuiz performance issues and found this.  Take it easy.  It is only his second post.  Plus, there are moderators here.

Ftr: I haven't noticed any performance issue on my lappy even with almost everything set to high.
Nvidia Geforce 9800M 512MB
4GB DDR2 RAM
Pentium Dual Core 2.24 GHz
Fedora 11

---

### Post by hhh on 2009-08-09
Woops, didn't look to see if it was a n))b or not, point taken;~)

---

