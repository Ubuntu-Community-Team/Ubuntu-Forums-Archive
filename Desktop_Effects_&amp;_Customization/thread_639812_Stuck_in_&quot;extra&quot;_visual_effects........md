---
title: "Stuck in &quot;extra&quot; visual effects......."
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by babygirl on 2007-12-13
AMD Athlon 64 3500+
2 gigs Crucial ddr 400
Nvidia Geforce 7300GT with 512 DDR2 onboard
Creative Sound Blaster Live! 


I'm trying to get my BF into Linux. So far he's VERY impressed with the visual effects, but I can't seem to get more than "extra". I have fully configured Compiz-Fusion so I think it may lie in the ATI chipset. Can anyone help me please?

I'm also having trouble getting Gutsy to keep my Creative audio as default. it works and I would like to enable 5.1 if possible, but it keeps reverting to the MB's onboard audio after reboot. 

I'm not a complete novice in Ubuntu, but I am pretty basic. I can navigate the file system ok too so I'm fairly capable. Please help!

---

### Post by babygirl on 2007-12-13
AMD Athlon 64 3500+
2 gigs Crucial ddr 400
Nvidia Geforce 7300GT with 512 DDR2 onboard
Creative Sound Blaster Live! 


I'm trying to get my BF into Linux. So far he's VERY impressed with the visual effects, but I can't seem to get more than "extra". I have fully configured Compiz-Fusion so I think it may lie in the ATI chipset. Can anyone help me get the "custom" effects?

I'm also having trouble getting Gutsy to keep my Creative audio as default. it works and I would like to enable 5.1 if possible, but it keeps reverting to the MB's onboard audio after reboot. 

I'm not a complete novice in Ubuntu, but I am pretty basic. I can navigate the file system ok too so I'm fairly capable. Please help!

---

### Post by Xp3reMental on 2007-12-13
Hallo and welcome...

I'm also a total newbie but atleast I know how to help you with the Compiz hiccup!

To get custom settings you need to install the Compiz Settings Manager:)

```
sudo apt-get install compizconfig-settings-manager
```

copy paste this code into Terminal and Enjoy!:biggrin:

---

### Post by babygirl on 2007-12-13
> **Xp3reMental said:**
> Hallo and welcome...

I'm also a total newbie but atleast I know how to help you with the Compiz hiccup!

To get custom settings you need to install the Compiz Settings Manager:)

```
sudo apt-get install compizconfig-settings-manager
```

copy paste this code into Terminal and Enjoy!:biggrin:


I've done that and FAR more. It's not Compiz, it's the ATI chipset. I have the same settings on my own PC and everything works purrrfectly. The only REAL difference in this system and mine is mines duel core with AMD chipset. As this machine is single core (same CPU) with ATI chipset. Are there any drivers for ATI chipsets?

Or could it be as simple as this machine isn't powerfull enough for "custom"? I have access to the custom menu, and I can set it to custom, but as soon as I turn custom on it turns it off. I have a lot of them running on my machine and I wouldn't doubt this one isn't powerfull enough. There very impressive. My machine finally runs like what I expect a machine too!!

---

### Post by le_jawa on 2007-12-13
Babygirl,

Your system specs show a GeForce 7300 and 2GB of RAM; processing power is not the problem!  ;-)

You may have already done this, but I'm going to ask, since you didn't specify it.  Have you installed the restricted driver for GeForce cards yet?   This would definitely cause fits.  Alternatively, have you compiled and installed the driver from [www.nvidia.com?]("http://www.nvidia.com?")  Doing either of these is essential for desktop effects.

Also, what Ubuntu release are you using on the machine with the problems?

Let us know!

Jason

---

### Post by babygirl on 2007-12-13
> **le_jawa said:**
> Babygirl,

Your system specs show a GeForce 7300 and 2GB of RAM; processing power is not the problem!  ;-)

You may have already done this, but I'm going to ask, since you didn't specify it.  Have you installed the restricted driver for GeForce cards yet?   This would definitely cause fits.  Alternatively, have you compiled and installed the driver from [www.nvidia.com?]("http://www.nvidia.com?")  Doing either of these is essential for desktop effects.

Also, what Ubuntu release are you using on the machine with the problems?

Let us know!

Jason

All drivers are installed and fully configured. I wouldn't be able to run any of the Compiz-Fusion stuff if otherwise. It has to be the ATI chipset. I've read soooo many other posts about people having problems with ATI stuff. In contrast I rarely hear anyone talk about AMD chipsets.

I'm running 7.10 Gusty

---

### Post by le_jawa on 2007-12-13
It quits as soon as it starts, eh?  I wonder if it's leaving a log entry.  Go to your System Menu, and Administration under that.  Then open your System Log applet.  Check all the logs under there and see if a message is being left.  Xorg.0.log is the most likely one to contain useful info, but is not necessarily the only place to find something like this.  If you find something useful (an error from ccsm) post it here.

Good luck!

Jason

---

### Post by le_jawa on 2007-12-13
I almost forgot; if you want to keep Ubuntu from using the on-board audio, reboot your PC and get into the BIOS settings.  From there, disable the on-board audio.  That will turn it off at the hardware level and should keep it from interfering in the future.


Once again, good luck!

Jason

---

### Post by babygirl on 2007-12-13
> **le_jawa said:**
> It quits as soon as it starts, eh?  I wonder if it's leaving a log entry.  Go to your System Menu, and Administration under that.  Then open your System Log applet.  Check all the logs under there and see if a message is being left.  Xorg.0.log is the most likely one to contain useful info, but is not necessarily the only place to find something like this.  If you find something useful (an error from ccsm) post it here.

Good luck!

Jason

No logs at all. I even turned them on, let it do the same thing, and went to check again and still nothing.

And thankies for the hardware tip! I never would have thought of that but I know exactly what yer talking about. Hope this BIOS has that option.

---

### Post by le_jawa on 2007-12-17
Ok, so no logs.  Let's try this then.  Instead of checking the logs, let's see if the program is throwing an error to stdout when it's run.  To catch it, open the GNOME terminal (not a "run program"-type dialog box, but an actual terminal emulator) and run ccsm from there (just type ccsm at the prompt and hit <Enter>.

If it gives you an error message, then just report it here.

Here's what's eatin' me: you reference multiple complaints about XGL and ATI chips, and they are out there.  The thing is, most of those comments are about ATI video chips and cards, not motherboard chips (at least from what I've seen).  It seems unlikely that the motherboard chipset is the problem, but we'll see.  Let us know how it goes.

Good luck!

Jason

---

### Post by babygirl on 2007-12-17
> **le_jawa said:**
> Ok, so no logs.  Let's try this then.  Instead of checking the logs, let's see if the program is throwing an error to stdout when it's run.  To catch it, open the GNOME terminal (not a "run program"-type dialog box, but an actual terminal emulator) and run ccsm from there (just type ccsm at the prompt and hit <Enter>.

If it gives you an error message, then just report it here.

Here's what's eatin' me: you reference multiple complaints about XGL and ATI chips, and they are out there.  The thing is, most of those comments are about ATI video chips and cards, not motherboard chips (at least from what I've seen).  It seems unlikely that the motherboard chipset is the problem, but we'll see.  Let us know how it goes.

Good luck!

Jason

No errors. It opened the settings manager purrrfectly. I have checked his MB manual, it is an ATI chipset, but I can't remember which family. Other than that this is a good system. 

I have another question...I just screwed a really old AMD K6 system to a piece of plywood and everything works just fine. But I can't get it to boot toUbuntu linux live disc. It gets where the little orange bar stops bouncing back and forth and started acualy showing progress. Then it seemed to be frozen and it skipped into the text based install and finally just quit loading altogether. Any ideas?

---

### Post by le_jawa on 2008-01-13
Babygirl,

Sorry it's been so long since I posted.  I'm afraid I got busy and forgot about this thread.  I was hoping someone else had picked up, but evidently not.

In any case, I'm running out of ideas.  One thing that does come to mind is to switch video cards between the two systems and see if it could be a problem with the card.  I know it's not likely, but it may be worth a shot.

The only other thought I have is to ask on the forums at the Compiz-Fusion website to see if they have any ideas regarding the ATI chipset or anything else.  I'm sorry I don't have more.

As for your old K6 system, I gotta say I LOVE the plywood setup.  I have no idea of why you did it, but that is really original (practical, not so much, but very original ;-) ).  I do have a few thoughts on the boot problems there.  Basically, it's probably a video problem (as if you needed more of those).  Try using the different boot modes on the CD to boot it and see if one of them will fix it.  That should do it.  If not, post back here and we'll try some kernel parameters.  Of course, trying a different vid card with it may do the trick.

As a small request, any chance you could post of photo of the rig?  I'm just curious to see what you've built with plywood.

Good luck!
Jason

Quick edit: make sure your live CD is clean and scratch-free, and try running a cleaning CD through that old CD-ROM drive.  That lens may be dirty and the source of the whole trouble.

---

