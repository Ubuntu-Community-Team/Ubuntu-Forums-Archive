---
title: "Issue with Jaunty freezing"
date: 2009-06-15
forum: General Help
---

### Post by RubberChipmunk on 2009-06-15
This is a rather irritating issue. I don't even know what causes it, because I'll be away from the computer for a few hours, return, and now everything is locked up. Keyboard doesn't respond, mouse doesn't respond, power button on my computer's case doesn't respond. I have to cut the power using my power director to restart it, at which point it will boot and run fine, until, of course, whatever is causing this problem happens again while I'm watching TV or something, and I come back to a frozen computer.

This started happening about a week or so ago, and I don't recall making any changes to my system around that time. Its happened at least ten times now, sometimes twice in a day, some days not at all, but then I'll wake up to a frozen computer.

Has anyone else had this problem? Have you solved it? How?

Any ideas as to why this might be happening?

---

### Post by synapsys on 2009-06-15
It sound like an issue with your hardware.... not with ubuntu. It may be overheating. When was the last time you cleaned the dust out of your computer?

---

### Post by procras on 2009-06-15
(1) If you have another box on your local net try to ssh into the locked one to see if you can find a mad process with top etc.

(2) Main lockups I had were due to proprietry drivers like fglrx. Since the standard ati driver caught up with my card I have not used fglrx and had no lockups.

Are you using proprietry drivers on your system?

(3) My screensavers used to lock the system with the proprietry driver. Stop using a screensaver, just blank the screen.

(4) I did have firefox crashing and locking the X server, but not recently. ssh trick (1) might identify this or you could try to get to a different vt with <ctrl><shift><f1> etc.

(5) Overheating is possible, was it on a hot day? If you are on water cooling check that the resevoir is not running low on H20.

Adrian

---

### Post by RubberChipmunk on 2009-06-15
> **synapsys said:**
> It sound like an issue with your hardware.... not with ubuntu. It may be overheating. When was the last time you cleaned the dust out of your computer?

My computer stays pretty cool and gets nice ventilation, but I'll go ahead and clean the dust out regardless. Might have an effect, you never know.

> **procras said:**
> (1) If you have another box on your local net try to ssh into the locked one to see if you can find a mad process with top etc.

I don't have another box. I can ask my roommates, but to be honest, I'm not too sure how I would go about doing that.

> (2) Main lockups I had were due to proprietry drivers like fglrx. Since the standard ati driver caught up with my card I have not used fglrx and had no lockups.

Are you using proprietry drivers on your system?

I'm running the Creative Soundblaster XFi Linux Beta driver for my soundcard and the NVIDEA version 180 driver for my GeForce 8600GT. Neither have given me any problems in the past when I installed Jaunty or for the many months I used Intrepid.

> (3) My screensavers used to lock the system with the proprietry driver. Stop using a screensaver, just blank the screen.

I use no screensavers and I don't blank the screen. I turn off the monitor when I am not at my computer.

> (4) I did have firefox crashing and locking the X server, but not recently. ssh trick (1) might identify this or you could try to get to a different vt with <ctrl><shift><f1> etc.

It happens whether firefox is running or not.

> (5) Overheating is possible, was it on a hot day? If you are on water cooling check that the resevoir is not running low on H20.

Adrian

As I said earlier in this post, I get pretty good cooling on my box. I'll clean out the dust and try keeping my room a little cooler. Hopefully that will have some effect.

---

### Post by fillintheblanks on 2009-06-15
mine was locking up too, I think its because of the graphics card driver

I was using driver 180.51 from the NVIDIA site..

I uninstalled it and tried the 180.44 version from System > Administration > Hardware drivers

since then I haven't experience any lock ups

---

### Post by TwoWordz on 2009-06-15
I had this problem once with a 3d screensaver that was crashing. 

Try to use a 2d screensaver to see. 

You can also confirm if this is the problem or not by setting the screensaver to go after a minute and see if it crashes. 

TW

---

### Post by Chemical Imbalance on 2009-06-15
You may want to take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

You're not alone with the freezing beginning in Jaunty...

It's frustrated me to no end.

---

### Post by Laysan_A on 2009-07-02
> This is a rather irritating issue. I don't even know what causes it, because I'll be away from the computer for a few hours, return, and now everything is locked up. Keyboard doesn't respond, mouse doesn't respond, power button on my computer's case doesn't respond. I have to cut the power using my power director to restart it, at which point it will boot and run fine, until, of course, whatever is causing this problem happens again while I'm watching TV or something, and I come back to a frozen computer.

Welcome to the club. 

I used to have the same (sounds like, anyway) kind of freezes after I first upgraded. They went away, probably because I changed to a different kernel, but another kind, where my screen suddenly goes black (or the predominant window color), and all I can do is hold down the power button until until it shuts down, persists.

Hope you find a solution; some have reported finding various solutions, perhaps you will too.

---

