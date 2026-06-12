---
title: "Wanted: How to get rid of compiz-fusion guide"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by LouisvilleLIP on 2007-07-01
I broke my compiz fusion cube when I installed the upgrades on 6/28.  I see lots of guide about getting compiz/emeraled/xgl, but I haven't seen any about undoing the damage when it breaks.  If I can learn how to undo it, I can start over.  As it stands now, I'm not sure how to get things back to working condition.  Can anyone point me in the direction of a removal guide?

If anyone wants to tackle the broken-compiz-after-upgrades problem, below is the log from Synaptic:

Upgraded the following packages:
compiz (1:0.5.1+git20070626~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu0
compiz-core (1:0.5.1+git20070626~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu0
compiz-fusion-plugins-extra (0.0.1+git20070626~3v1ubuntu0) to 0.0.1+git20070627~3v1ubuntu0
compiz-fusion-plugins-main (0.0.1+git20070626~3v1ubuntu0) to 0.0.1+git20070627~3v1ubuntu0
compiz-gnome (1:0.5.1+git20070626~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu0
compiz-plugins (1:0.5.1+git20070626~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu0
compizconfig-settings-manager (0.1.0+git20070625~3v1ubuntu1) to 0.1.0+git20070627~3v1ubuntu0
libdecoration0 (1:0.5.1+git20070626~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu0

Upgraded the following packages:
compiz (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
compiz-core (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
compiz-fusion-plugins-main (0.0.1+git20070627~3v1ubuntu0) to 0.0.1+git20070628~3v1ubuntu0
compiz-gnome (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
compiz-plugins (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
libdecoration0 (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28) to 2.6.20.5-16.29
linux-restricted-modules-common (2.6.20.5-16.28) to 2.6.20.5-16.29
xorg-driver-fglrx (7.1.0-8.34.8+2.6.20.5-16.28) to 7.1.0-8.34.8+2.6.20.5-16.29

---

### Post by steveneddy on 2007-07-01
What, exactly, is the problem. I seriously doubt that it is Compiz-Fusion that is broken. It is likely that you didn't have your machine preconfigured for running 3D desktop environments or your video can't handle the GL environment.

Tell us about your hardware and why you think CF is broken.

What video card do you have?

Do you have the correct drivers installed for this card?

Have you been able to run Beryl or Compiz (the plain version) before this?

Is this your first attempt at a GL 3D environment?

EDIT:

Looking at some of your previous posts, you do know that is a difference between the Compiz-Fusion and Compiz plain, right?

Compiz-Fusion is controlled by the CompizConfig Settings Manager.

Compiz is controlled by the Desktop Effects Manager.

You may be changing settings in one and not getting the effect you are looking for because you are using the wrong manager.

---

### Post by steveneddy on 2007-07-01
> **LouisvilleLIP said:**
> 

Upgraded the following packages:
compiz (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
compiz-core (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
compiz-fusion-plugins-main (0.0.1+git20070627~3v1ubuntu0) to 0.0.1+git20070628~3v1ubuntu0
compiz-gnome (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
compiz-plugins (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
libdecoration0 (1:0.5.1+git20070627~3v1ubuntu0) to 1:0.5.1+git20070627~3v1ubuntu1
linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28) to 2.6.20.5-16.29
linux-restricted-modules-common (2.6.20.5-16.28) to 2.6.20.5-16.29
xorg-driver-fglrx (7.1.0-8.34.8+2.6.20.5-16.28) to 7.1.0-8.34.8+2.6.20.5-16.29

When my update mirroring this update you posted, it updated my video drivers as well. Are you using the binary drivers from the manufacturer of something available in the repos?

---

### Post by LouisvilleLIP on 2007-07-01
**Thanks for the help.  Let me know if you need more info.**

What video card do you have? **3.0 P4, ATI 9800 Pro, 1GB Ram.  Everything was working on 6/28 until I upgraded those packages.  My cube and rotation both worked.  There were some minor issues, but mostly everything was ok**

Do you have the correct drivers installed for this card? **I have no idea. It's possible I do not, I'm not sure how to tell.**

Have you been able to run Beryl or Compiz (the plain version) before this? **Haven't tried**

Is this your first attempt at a GL 3D environment? **Yes**

Looking at some of your previous posts, you do know that is a difference between the Compiz-Fusion and Compiz plain, right?  **Yes**

Compiz-Fusion is controlled by the CompizConfig Settings Manager.

Compiz is controlled by the Desktop Effects Manager.

You may be changing settings in one and not getting the effect you are looking for because you are using the wrong manager.  **I am using compizconfig settings Manager.**

---

### Post by steveneddy on 2007-07-01
> **LouisvilleLIP said:**
> 

Do you have the correct drivers installed for this card? **I have no idea. It's possible I do not, I'm not sure how to tell.**



OK - not being an ATI user, I use nVidia, if you have drivers that come from the manufacturer, not from the repos, that MAY be your problem.

Have you searched other posts for the same problem from others that use ATI?

I'm no expert here, but [this post]("http://ubuntuforums.org/showthread.php?t=480134&highlight=compiz+ati+upgrade") may help.


Some quotes from that thread.

> If you use the fglrx driver then you cannot use AIGLX, you need to use XGL.

Have a look at this:

[http://wiki.beryl-project.org/wiki/I...eisty_with_XGL](http://wiki.beryl-project.org/wiki/I...eisty_with_XGL)

Skip the step to add the new repositories, it is better to stick to Feisty original repositories to avoid creating inconsistencies.

> disable fglrx driver

This may send you down the correct path, but it is a place to start. I suggest searching the forums by using keywords, not phrases, to narrow down your issue. I'm sure that you aren't the only one with this problem.

Also, look at [this post]("http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+ati+upgrade") to see if it can help you get your Fission working.

---

### Post by LouisvilleLIP on 2007-07-01
Thanks for the find.  I originally got this working using a similar guide, but tried this and it fixed everything.  Thanks a lot, I've been looking everywhere for this answer.

---

