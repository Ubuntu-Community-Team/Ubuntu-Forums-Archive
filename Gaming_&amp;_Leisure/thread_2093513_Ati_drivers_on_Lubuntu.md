---
title: "Ati drivers on Lubuntu"
date: 2012-12-11
forum: Gaming &amp; Leisure
---

### Post by Extol11 on 2012-12-11
So I just got an invite for the steam beta. I switched to Lubuntu about a month ago and I have made it my default version. I ended up reinstalling the thing from scratch and now I don't have any other GUI on my linux installation. So I was wondering how do I install the ati drivers on Lubuntu. I know they're not working since even Chromiun (the open source rail shooter game) doesn't run well on the thing. I have an Ati 4890 on my PC and I used to use the restricted drivers options in the regular ubuntu. But that window is nowhere to be found on Lubuntu and the documentation on lubuntu.net doesn't say how to get them to work (afaik). Could anyone tell me if there's (preferably) a graphical way to install the drivers? I would like to know the drivers installed well and have some visual way to know they're working right (like the green light shown when you're using the ati driver in unity's restricted drivers window). But I'll use sudo apt-get if necessary. I just want to know to be able to get in the linux beta as soon as possible. Thanks.

---

### Post by mastablasta on 2012-12-11
did you check in software sources? i believe the driver installation programme moved there.
 
[http://www.upubuntu.com/2012/10/to-do-list-after-new-installation-of.html](http://www.upubuntu.com/2012/10/to-do-list-after-new-installation-of.html)
[http://www.omgubuntu.co.uk/2012/07/ubuntu-12-10-alpha-3-released](http://www.omgubuntu.co.uk/2012/07/ubuntu-12-10-alpha-3-released)

---

### Post by Extol11 on 2012-12-11
Thanks for the info. I'm giving it a try right now. I'm finding this less ideal than the previous way of installing the drivers. I liked just clicking that one checkbox and getting them installed right away.

---

### Post by Extol11 on 2012-12-11
For some reason the fglrx drivers set my resolution to 1280 x 800 leaving a black frame around the image. My monitor can go up to 1920 x 1080. Do I need to configure something after this or is my card no longer supported? This is the first time I've had this happen.

Edit: Also, even though the drivers are installed, software sources says there are no propietary drivers in use.

---

### Post by mastablasta on 2012-12-11
Ati 4890 - you need to use 12.04 i think. 2xxx, 3xxx, 4xxx support was dropped i belive. not sure though. or you can install legacy driver with a PPA.
Not using LXDE to knwo where to change resolution (if that is the only issue)

---

### Post by Extol11 on 2012-12-11
Do you mean the 12.04 version of Ubuntu or some old drivers? But official Ubuntu documentation is a bit lacking at the moment. I guess I'll have to reinstall 12.04 soon then. I'll see if I can get the PPA for them. Thanks for the help.

---

### Post by Extol11 on 2012-12-11
Ok. I found this information and this is the cause of the problem. I only wish it would have been in the official documentation.

[http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)

I'll compile the legacy driver tomorrow since I don't have time for it atm. But once I compile it, I doubt I'll run into anymore trouble. Thanks for all of the help.

---

### Post by QIII on 2012-12-11
DON'T BOTHER with the legacy driver as described there.  The script downgrades X Server to 1.12 from 1.13.  It doesn't fix the problem, it kludges a work around.  You'd be stuck with a legacy driver and an old version of X Server.

That driver will not work with the version of X Server used by 12.10.

The only way you can use the proprietary driver is if you have an HD 5xxx card or later.

12.04 is the end of the line for your card unless you use the open source Radeon driver from Quantal forward.

So, short of buying a new card, your choices are Precise and the legacy proprietary driver or Quantal and the open source driver.

The open source driver is very good now and will suit the needs of the vast majority of users.

If you simply MUST have the proprietary driver for some reason, it would be better to go back to a whole LTS than move forward with a broken Quantal.  You'd have 5 years of service from a properly configured system.

And the 12.4 driver is in the repo, so you wouldn't have to install from the ATI website.

I am a bit frustrated with this whole thing.  AMD/ATI is a member of the Linux Foundation.  I don't remember seeing anything in my newsletters about this by way of warning.  They left the community in a lurch with this -- and there are still NEW products being delivered with HD 4xxx GPUs!

---

### Post by mastablasta on 2012-12-12
> **QIII said:**
>  They left the community in a lurch with this -- and there are still NEW products being delivered with HD 4xxx GPUs!
 
yes it is strange. perhaps they ment that opensource drivers are just as good. though i doubt it. it's actually too bad they don't develope them opensource or at leats they could open the source if they drop official support.
 
oh well, i plan to go LTS anyway.

---

### Post by Extol11 on 2012-12-12
I think I'll make my life simple and just downgrade to 12.04. The bummer is LXDE looks so much sweeter on 12.10. Oh well... This sucks. Time to gather some money for a new card.

---

### Post by mastablasta on 2012-12-13
you can update only LXDE via PPA. i used to have it like that in 10.10 (updating only KDE via PPA) becuase it had some additional funcitons i needed/wanted. with 12.04 i don't have the need to do it. but you can do it if you wish.

---

### Post by Extol11 on 2012-12-13
Ok guys. The graphics driver from that PPA in that article I posted actually works. I did not have to uninstall or downgrade Lubuntu, it works. So I wanted to let you guys know that. Thanks to everyone who helped and gave advice and Thanks Mastablasta for that last bit of info as well. So just use that repository in the mean time.

---

### Post by QIII on 2012-12-14
Just be aware that it downgraded your X Server from 1.13 to 1.12 and you are not running a complete Quantal.

---

### Post by Extol11 on 2012-12-14
> **QIII said:**
> Just be aware that it downgraded your X Server from 1.13 to 1.12 and you are not running a complete Quantal.

I just now noticed that Amnesia the Dark Descent runs fine but Team Fortress 2 does not want to load. So I suppose that's the reason. I wanted to give this heads up.

---

