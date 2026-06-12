---
title: "Need help: Desktop area beyond the screen size"
date: 2009-04-16
forum: Desktop Environments
---

### Post by irate.turtle on 2009-04-16
I have a dell studio 15 laptop with 8.04

---
My problem is that the after startup the desktop area is 2560 x 800 while my laptop monitor is only showing the 1280 x 800 of it.

Basically while ubuntu is showing a wide desktop area, my laptop screen is only showing the left half of it.
---
The problem goes away if I refresh the resolution from within the ATI Catalyst Control Center (ATI-CCC) , i.e., the desktop area becomes 1280 x 800. But after restart system it becomes 2560 x 800 again.
---
Earlier I had attached an LCD monitor to the laptop and used ATI-CCC to setup dual monitor. So I think somewhere the settings have stuck onto that and thus the display still publishes material for the LCD screen even though it is not there.
---
I tried to search any similar problem posted. [**_This post_**]("http://ubuntuforums.org/showthread.php?p=248755") mentioned resolution issues which get reset with each startup. It suggests changing resolution value in /desktop/gnome/screen/default/0/ but when I open gconf editor there is no key 'screen' within /desktop/gnome

How to fix this? Till now I didn't have any major problems but now I am using other sessions and only half the error message gets displayed on my laptop screen and rest remains hidden from view.

---

### Post by Sarai the Geek on 2009-04-16
Well, I don't know a whole lot about ATI cards, but you should take a look at this, it might help: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by irate.turtle on 2009-04-17
> **Sarai the Geek said:**
> Well, I don't know a whole lot about ATI cards, but you should take a look at this, it might help: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Let me try it out. Will get back in sometime.

---

### Post by irate.turtle on 2009-04-24
> **Sarai the Geek said:**
> Well, I don't know a whole lot about ATI cards, but you should take a look at this, it might help: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

After I took the steps mentioned on that thread to reconfigure my Xorg, it started showing all pretty fuzzed up and nothing would display right.

Then after some more online digging I used

aticonfig --initial --dtop single

to reconfigure my xorg.conf and it fixed both the break and the resolution issue.

My guess is that probably reconfiguration of Xorg was redundant but not sure.

Thanks

---

### Post by Sarai the Geek on 2009-04-24
> **irate.turtle said:**
> After I took the steps mentioned on that thread to reconfigure my Xorg, it started showing all pretty fuzzed up and nothing would display right.

Then after some more online digging I used

aticonfig --initial --dtop single

to reconfigure my xorg.conf and it fixed both the break and the resolution issue.

My guess is that probably reconfiguration of Xorg was redundant but not sure.

Thanks

Great to hear!

---

