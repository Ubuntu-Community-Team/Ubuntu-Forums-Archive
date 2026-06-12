---
title: "Volume buttons too aggressive in 8.10 on Dell m1330"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wbrendel on 2008-11-08
I am having a problem with Ubuntu 8.10 on my Dell m1330. I originally had Hardy installed, and I did an upgrade to Intrepid (upgraded, not a clean install). In Hardy, the volume buttons on my laptop worked fine. The up/down volume buttons increased/decreased the volume by about 8-10% I'd guess.

Now in Intrepid, the volume buttons decrease the volume by 18% and increase it by 23%. Has anyone else run into this issue? Again, everything was working in Hardy. I should also mention that just before upgrading to 8.10, I applied a BIOS update from version A11 to A12. I can't imagine the BIOS update changing anything with the volume buttons, but I thought I would mention it for the sake of completeness.

Thanks!

**EDIT:** I played around with the "Repeat Keys" section of the Keyboard Preferences window. Unchecking the "key presses repeat when key is held down" checkbox solves the volume control problem, but it makes typing in general annoying. Help? :-(

**EDIT 2:** With a little more tinkering, I was able to "fix" the problem. I increased my repeat delay a bit, and decreased my repeat rate by just a hair. The littlest change to those values got the volume control working properly again.

-Will

---

### Post by elgreengeeto on 2008-11-08
I'm having a similar but worse problem on my X61 thinkpad after upgrading to 8.10 (wow a lot of stuff broke with this update for me! >_< )

I tried messing with the key repeat. Even turning it off did nothing for me. What's even more annoying is now the volume keys control ALL the tracks in my ALSA mixer, not just the master. That means if I turn up the volume using the volume key the internal mic becomes un-muted and I get nails-on-chalkboard feedback.

Anybody have idea where the configuration for the action of the hardware volume keys might live?

EDIT: found the last post here and it fixed it! why didn't I think of checking that??:

[http://tennessee.ubuntuforums.com/showthread.php?p=6033836](http://tennessee.ubuntuforums.com/showthread.php?p=6033836)

> discovered on my Sound preferences that PCM was selected for keyboard control instead of Master. Changing it to Master made everything work right

---

### Post by superm1 on 2008-11-08
This is likely the Dell specific bug you are seeing:

[https://bugs.edge.launchpad.net/ubuntu/+bug/261721](https://bugs.edge.launchpad.net/ubuntu/+bug/261721)

There is an upload that should be in intrepid-proposed early next week that resolves it.

---

### Post by mbeach on 2008-11-11
my dell studio 1735 brightness (fn + up/down) are working correctly now after an update to 2.6.27-8

---

