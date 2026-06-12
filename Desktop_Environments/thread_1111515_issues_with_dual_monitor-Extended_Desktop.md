---
title: "issues with dual monitor-Extended Desktop"
date: 2009-03-30
forum: Desktop Environments
---

### Post by arrow.69 on 2009-03-30
Hi,

I just recently installed Ubuntu 9.04 Beta on my laptop.  I run a dual monitor set up which I've never been able to get to work properly in Linux.  I was hoping it would work in this new version so I gave it a try.  Indeed, the display settings seem to be much more straightforward.  I can either choose Mirrored or Extended Desktop, and both worked out of the box.

I do have one issue with the Extended Desktop setting.  What it seems to do is act as though my two monitor were one huge screen.  This is fine, except that when I maximize a window, for example, it spans across both screens.  When I watch a movie, it distorts it by stretching it to both screens.  Compiz effects like Switcher happen in the 'middle' of the screen, which means I can't really see it happen.  Also, alot of applications start in the 'middle, which is an annoyance since they'll be split between both screens.

What I want is a setup where I can choose which screen to use as my primary one, with panels, Switcher, on that one, and the other screen blank, so I can drag an application and run it onto that window.  But most of all I just want my windows to maximize on one screen or the other.  Otherwise the extended desktop is completely unusable.  Does anyone have an idea of a workaround or configuration that would solve my problem?

Thanks

---

### Post by Sam Lars on 2009-03-31
Some of the Compiz plugins have options for how they handle multiple screens... whether they appear in the middle or on one, both, etc.
It also could be a bug... what video card are you using?

---

### Post by arrow.69 on 2009-03-31
Thanks for the reply,

I'm not so much worried about the compiz plug-ins, which are a minor annoyance, as much as I'm concerned about my other applications.  Firefox, for example, will stretch across both screens.  So will VLC in full screen mode.  My Video Card is an ATI HD3700 or something.  I'm not quite sure if this has anything to do with the problem but when I go into my ati catalyst control center, the options for Xinerama are greyed out because apparently, I only have one desktop enabled.  Not quite sure what that means.

---

### Post by kg6gfq on 2009-03-31
The same problem is being discussed at [http://ubuntuforums.org/showthread.php?p=6989196#post6989196](http://ubuntuforums.org/showthread.php?p=6989196#post6989196) 

I think it's a bug in ATI's drivers.  Seems like complaints should be sent to them since it's a proprietary driver, but I'm not sure how...  Guess I'll go have a look on launchpad.

---

