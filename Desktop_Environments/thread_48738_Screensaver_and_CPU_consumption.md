---
title: "Screensaver and CPU consumption"
date: 2005-07-13
forum: Desktop Environments
---

### Post by McAviti on 2005-07-13
Hi Folk!

I like the really fance screensaver of my KDE desktop; nevertheless, many of them are pretty fast but also push CPU usage up to 100% making my CPU fan spinning annoyingly (and also waste energy heating up my sommerly hot flat).
So - is there a way to throttle the screensaver down to a decent CPU usage, even when the colorful patches don't swirl around so fast around anymore. :)

~k

---

### Post by skyboy on 2005-07-14
That depends on your Graphic card and your config.
Tell us a bit more about your equipment.
Indeed, if your graphic card doesnt have onboard accelaration, the problem might be that the cpu has to do the job, especially if you use really fancy screensaver (eg. openGL)
your screensaver isnt static is it ? :)

---

### Post by McAviti on 2005-07-24
Hi!

Thanx for your reply and sorry for not answering yet - i was kind of knocked off the last week.
Well, I have a rather standardized system, it's a CPQ/HP PC with 2,4 GHz CPU. The graphics card is one from nVidia:
--
Section "Device"
        Identifier      "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
--
So well, yep, I do indeed use fancy screen savers (randomny selected), and some of them are pretty fast, using hardware accelleration indeed. That speed seems to be the problem, the screen savers seem to try to move their items as fast as possible, using every cpu cycle available. This leeds to a start of the CPU cooling fan and my PC becomes a heating agent in my already to warm flat.
I recently changed from a suse linux installation; I'm not 100% sure of that, but I think the fan did not start when the more sophisticated sreen savers started up.
So - my question was if there's some way to talk the screensaver not using more than e.g. 50% of CPU time (or less) to keep the thing a little bit cooler.

thanxalot for caring,
~klemens

---

### Post by skyboy on 2005-07-25
well, nothing very easy come to my mind right now but you can try to setup the priority of the screen savers. Configure Desktop -> ScreenSaver -> advanced option -> low priority

I'll think about anything else but without hacking the code, i am not sure it is possible.

Maybe you can try to check powernowd. On ubuntu, it is reasponsible for the CPU step management.

---

### Post by McAviti on 2005-07-26
thanks for your tips. anyway, the screensaver attribute is already set to low prio, i assume that this makes it only nicer when competing with other processes for cpu cycles.
i also had a look at powernowd, but my intel desktop cpu doesn't seem very impressed. so for now i just deactivated the opengl screen savers, the other ones seem to not use all cpu if available.
nevertheless, the way my system and the screensavers behave seem somehow normal to me. i'm really curious how suse did the trick in my former installation... (-;

thanx again.

---

### Post by mapman on 2005-08-09
I too am experiencing high cpu usage with the screensavers, specifically opengl with a 2.4gig cpu and even had a freeze last nite with the lattice screensaver.  I didn't have much luck getting out of the lock by pressing ctrl,alt,backspace or even getting into another login..initially.  After about a minute of doing nothing x eventually restarted (ctrl,alt, backspace must have kicked in eventually).  Is there something i should enable or disable in my xorg.conf ?  Is there a description somewhere of the different options one can set in xorg.conf and why?(i've seen many posts about enabling and disabling certain options but never many reasons of why....)  Am i on the right track in assuming it may be with the xorg.conf? (can post if needed,there aren't any video card options set up, similar to McAviti's....)

---

### Post by mapman on 2005-08-09
Anyways I think I fixed the problem of the lattice screensaver freezing up by installing the nvidia drivers instead of nv.  The 3d performance is excellent!  But the cpu still maxs out, so maybe that's just the way it is for the 3d intensive screensavers (unless someone out there tells me otherwise...).  Found a man page on the xorg.conf online that may be helpful to anyone (probably is with the ubuntu install too)......

[http://www.die.net/doc/linux/man/man5/xorg.conf.5.html](http://www.die.net/doc/linux/man/man5/xorg.conf.5.html)

---

