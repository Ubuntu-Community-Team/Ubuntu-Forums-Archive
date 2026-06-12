---
title: "Ubuntu on Dell Inspiron One 2320?"
date: 2012-01-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vmalep on 2012-01-01
Hi,

I am looking for a all-in-one desktop compatible with Ubuntu and the [Dell Inspiron One 2320]("http://www.dell.com/us/p/inspiron-one-2320/pd") seems a good choice. However, I had bad experiences with the last computers I bought and I want to make sure it would work fine.

Has anyone tried?

It is running on a Intel® Pentium® G620 Processor (2.60GHz, 3MB) and has a Integrated Intel® HD Graphics 2000 graphic card (for which I have some doubts: [http://ubuntuforums.org/showthread.php?t=1791325]("http://ubuntuforums.org/showthread.php?t=1791325")).

Also it has a touch screen and I am wondering if it would work fine...

Thanks for your feedbacks!
Pierre

---

### Post by Axv129 on 2012-01-02
I have one and I can tell you that I'm having a lot of problems getting the graphics card working correctly.  It does not recognize the resolution of the screen and I'm stuck with 1024x768.  It seems to be poor support for the sandy bridge integrated graphics.  Ubuntu will not show anything on the main screen during a boot, unless the 'nomodeset' option is added.  OpenSuse boots fine, but the display is still limited to 1024x768.  However the touchscreen and everything else works right off the bat.

---

### Post by dbrown11_can on 2012-01-16
I bought a 2300 with an Intel 2600 and an Nvidia graphics card.  We tried Ubuntu 10.04 and 12.04 (Beta).  It appears that the Sandy Bridge GPU is connected to the screen rather than the Nvidia card.  We can use the Nvidia for signal processing tasks but not for writing the screen - we suspect that the designers might have anticipated using the Sandy Bridge as a frame buffer.  However we haven't found the magic drivers to allow Xorg to find the screen through the Sandy Bridge GPU.  X reports that there is no monitor present when we try to configure the Nvidia card in X.

Dell tech-support has shortened my life by an hour with no benefit.

Also bought an HP Touch-Smart 9300 Elite All-in-One.  It also has an Intel 2600 (Sandy Bridge Quad-core) and a slightly different Nvidia GPU.  Ubuntu 10.04 worked on it out of the box, touch screen and all.  It does NOT have a TV tuner or blu-ray player, just a DVD player.

---

### Post by agnisflugen on 2012-08-21
I'm seriously considering buying a Dell Inspiron One 2320 but wanted to get some advise first. Is anyone using this PC as a dual boot? Are there any potential problems I should be aware of? I'm very much a novice on Linux. My only experience is running 10.10 maverick on my little ASUS Eeepc 1215T, so I'm looking to upgrade my system (hahaha) but I don't want to become overwhelmed by purchasing something that needs tweeking beyond my basic understanding.

---

### Post by robertj20112 on 2012-09-12
> **agnisflugen said:**
> I'm seriously considering buying a Dell Inspiron One 2320 but wanted to get some advise first. Is anyone using this PC as a dual boot? Are there any potential problems I should be aware of? I'm very much a novice on Linux. My only experience is running 10.10 maverick on my little ASUS Eeepc 1215T, so I'm looking to upgrade my system (hahaha) but I don't want to become overwhelmed by purchasing something that needs tweeking beyond my basic understanding.

I am running a 2320 dual-boot with Windows 7.  No problems with the dual-boot aspect, but I am having the video resolution problems (in 12.04) mentioned in the second post above.  Limited choices of screen resolution, none in the 16:9 ratio, with the result that screen is stretched horizontally...not acceptable to my wife, whose computer it is.  So she still is using Win7 until I can find out the solution to this problem, if any.

---

