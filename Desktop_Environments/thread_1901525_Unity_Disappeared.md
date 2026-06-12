---
title: "Unity Disappeared"
date: 2011-12-28
forum: Desktop Environments
---

### Post by Robing Goodfellow on 2011-12-28
**_Was:_** HP 64 bit HP G62 laptop w/ radeon 4200 running Oneiric with unity
**_Is:_** Same machine running Maverick with Gnome 2.x

didn't change my system, didn't add any effects, did some work in NetBeans, checked my mail, closed the lid and went to bed.  Woke up yesterday morning, NO UNITY.  NOTHING.  Top bar useless.  All my data and apps were still there, popped into terminal was able to do whatever I needed, but still.  This.  Ain't.  Quite.  Right. Logged out, logged in, same same.  Restarted the machine, no joy.

Accused the 20-somethings of messing with my laptop.  Nope.  Honestly, none of them motivated or smart enough to really do any damage on a Linux system.

No unity.  Rassfrrassn!!! Shyte.  I miss it.  I had actually not only gotten used to it, but had started to begrudgingly like it.

Until it disappeared.  --reset did no good, nor ccsm advice found elsewhere on the forums and the net.  No freakin unity.  Dumped the system, re-installed Maverick.  Does anyone have a concrete fix or have any idea why this is happening?  It appears to be happening to a lot of people, but not quite the way it happened to me, hence the new post. 

I Spent the day working on Maverick, thinking about changing distros, but hate to give up on Ubuntu.  It would feel like going out and getting some strange.  

But I can't stick with a system that fails without me causing the failure. :D

Anybody have any ideas besides --reset or "make sure this and that are checked in ccsm"?

regards, Richard

---

### Post by lolpenguin on 2011-12-28
So...let's clarify the situation...
This happened on your Oneiric laptop, right? You closed the lid, and the next day, Unity decided to go AWoL.
Log out, and log in to the Ubuntu session. This is the Unity session.
```
Logged out, logged in, same same. Restarted the machine, no joy.
```
So this should be a repeat of logging out and back in.
Now log out again, and log into Ubuntu 2D. It provides the same functionality as Unity, but doesn't look as good. Since it doesn't require 3D acceleration, it should use less memory and work faster.
Can't think of anything else though...:(

---

### Post by wildmanne39 on 2011-12-28
Hi, one thing I noticed when I first installed 11.10 was that the unity plugin came unchecked a couple of times and I just opened ccsm and rechecked it and it was working again.
Thanks

---

### Post by Robing Goodfellow on 2011-12-28
Thanks for the help.  Tried both of those (logging out, logging back in; logging in to 2D; opening ccsm ensuring unity was checked {it was})

regards, Richard

---

