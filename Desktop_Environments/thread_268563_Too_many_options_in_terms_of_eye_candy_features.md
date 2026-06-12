---
title: "Too many options in terms of eye candy features"
date: 2006-09-30
forum: Desktop Environments
---

### Post by horatiub on 2006-09-30
I would like to install Ubuntu on my laptop, I have an ATI X600 card, and I just can't figure out all the options that are available out there. 

Should I go with XGL? AIGLX? Compiz or Beryl? Am i better off trying Edgy with one of the above options? I've been reading these forums and I still can't figure out what to choose

---

### Post by orb9220 on 2006-09-30
First you need to install the i386 desktop dapper 6.06.1  [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

And learn the basic of a few command in the terminal. Then you will  need to learn where and how to edit your fstab and xorg.conf file. How to install support packages for video and audio.

Having a laptop you may have more problems getting everything to work in dapper alone worrying about xgl,compwiz,beryl which is what I run on desktop with dual monitors.

But only after I spent a month learning the basic's.
For a laptop I wouldn't even consider trying edgy until the official release at end of Oct. when most of the major bugs should be worked out.

Goto the edgy thread and read all the post's to start learning the pro's and con's.

And if you try to rush for eye candy then you will probally poke your eye out.

---

### Post by djRobbieF on 2006-09-30
> **horatiub said:**
> I would like to install Ubuntu on my laptop, I have an ATI X600 card, and I just can't figure out all the options that are available out there. 

Should I go with XGL? AIGLX? Compiz or Beryl? Am i better off trying Edgy with one of the above options? I've been reading these forums and I still can't figure out what to choose

First things first; you need to know what in the world you're talking about.

XGL *or* AIGLX = XGL, because you have an ATI card.

Compiz *or* Beryl = Compiz IS Beryl... or vice-versa.  Compiz is old.  Beryl is new.  The answer is: BERYL.  Unless you want to be using something old and buggy.  (Don't start a debate, those who know that Beryl is just a fork... I'm just trying to keep things simple for horatiub...)

XGL, Beryl.

Problem solved.

---

### Post by cmost on 2006-09-30
DJRobbie, I think you're over simplifying a bit.  It's imperative, in light of the abundance of choice (we are spoiled here in the FOSS community) to understand a few basic concepts:
1.  First, XGL is an xserver, just like X.org, except with acceleration (with XGL, everything you see on screen is pre-drawn by the graphics card using its enhanced chipset and then mapped to the display.)  XGL is NOT equal to AIGLX.  XGL was written from scratch as a band-aid, so to speak, until X.org could catch up.  It also enables nVidia cards to implement accelerated desktops as it's able to use the GLX_EXT_texture_from_pixmap function from MESA, instead of the graphics card driver (which lacked the function until just recently.)

2.  AIGLX is simply an extension of X.org (classic X server) that essentially accomplishes the same thing as XGL but without reinventing the wheel.  It requires the GLX_EXT_texture_from_pixmap function in order to work properly.  Now that both nVidia and ATI support this function with their upcoming new drivers, AIGLX will eventually cause XGL to fade away.

3.  Compiz is the compositing manager that enables all the cool 3D effect's you've no doubt seen images of ad nauseum!  It's a Window manager that sits on top of XGL or AIGLX and manages the windowing environment to spectacular effect.  Compiz was implemented by Novell in SUSE Linux Enterprise Desktop 10.0 and it eventually made it's way into the FOSS version, SUSE (now OpenSUSE 10.1.)

4.  A group of hackers lead by someone named Quinnstorm, got together and took Compiz and extended it with even more cool effects while also fixing many bugs and implementing other features.  When the Quinn version of Compiz grew too far from the original Compiz, that group forked the project to form Beryl.  For all intents and purposes, Beryl is simply an alternative to Compiz.  Personally, I think it's really REALLY cool.

Both XGL and AIGLX are easy to setup.  AIGLX is especially easy since it's built into X.org 7.1 and enabled by default.  XGL is also easy to setup in my opinion, but some users report stability problems.  My adivice would be to wait for Edgy GOLD, then use AIGLX with supported drivers for your ATI card.  Then it will simply be a matter of choosing Compiz or Beryl.  I hope this helps.

---

### Post by djRobbieF on 2006-09-30
> **cmost said:**
> DJRobbie, I think you're over simplifying a bit.

Yes, you're right.  This user wanted over-simplified, and I gave it to them  :)

True, we'll be golden with Xorg 7.1 - but that won't be until edgy... this user is most likely installing Dapper, as they don't strike me as the beta-tester type.

In summary, for now, XGL and Beryl is most likely the best "easy" solution for this user, that's all.  Until edgy is stable, it's probably the best solution in this case.

...without over-complicating it for someone who is not quite ready to learn how everything works under-the-hood.

---

### Post by djRobbieF on 2006-09-30
BTW, cmost, your explanations are very good.  Cheers.

---

### Post by horatiub on 2006-09-30
thank you to all that responded.

I know that somebody gave me an advice to start learning the commands first and then play with the eye candy :), but I'm not really a newbie, I've been running a debian server for the past 2 yrs, but that's beside the point.

I also read and learned about the differences between XGL and AIGLX, but the confusing part in my case is the drivers support. Some people mention that there are drivers for AIGLX with an ATI card, some say they're not, so this is where I'm really confused about it.

I will probably install Edgy beta since I don't mind the little bugs, and it has Xorg 7.1 and other newer things

---

### Post by mindless on 2006-09-30
@cmost

Has it been confirmed that ATI's drivers will support GLX_EXT_texture_from_pixmap?

---

### Post by horatiub on 2006-10-01
> **mindless said:**
> @cmost

Has it been confirmed that ATI's drivers will support GLX_EXT_texture_from_pixmap?

good question. Anybody?

---

### Post by cmost on 2006-10-03
From: [http://www.phoronix.com/scan.php?page=article&item=520&num=1](http://www.phoronix.com/scan.php?page=article&item=520&num=1)
Published: July 28, 2006

"Getting back on track with fglrx 8.27.10... First and foremost, ATI has beat NVIDIA to supporting X.Org v7.1 in their proprietary drivers. X.Org v7.1 is supported in the fglrx 8.27.10 drivers ***except for the GLX_EXT_texture_from_pixmap extension***. This OpenGL extension allows a color buffer to be used for both rendering and texturing, and is needed for AIGLX. ***We would not expect to see this extension supported by fglrx for at least a couple more months.*** X11R7.2 is already planned for release later this year. For reference, NVIDIA likely will not be delivering their 1.0-9XXX drivers with X11R7.1 support until August or September of this year. NVIDIA's drivers are expected, however, to support GLX_EXT_texture_from_pixmap. Another note about the X.Org 7.1 support is that X-Video with X1k products will not work, but it should be corrected in future releases."

The next version of the ATI driver will finally support GLX_EXT_texture_from_pixmap, hopefully!  Sorry guys for the confusion.

---

### Post by ashrack on 2006-10-09
so until ATI releases GLX_EXT_texture_from_pixmap FGLRX drivers, we how bought ATI GPUs must use XGL and not AIGLX?
And also does the ATI OpenSource driver support GLX_EXT_texture_from_pixmap so that it would be able to run AIGLX?

---

