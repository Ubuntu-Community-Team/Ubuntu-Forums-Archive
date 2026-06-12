---
title: "Dell Latitude C810 Issues"
date: 2007-07-03
forum: Dell  Ubuntu Support
---

### Post by Angelus7 on 2007-07-03
Alright...so, I have Ubuntu 6.06 LTS installed freshly on my Dell Latitude C810 laptop.  I had DBAN'd the hard drive earlier, so absolutely everything is fresh..

The problems I am having are as follows:

1.Random Mouse Lag:  About once every 10-15ish seconds, the mouse lags, hangs, or disappears.  It corrects itself, but ends up doing it sometime after, and the cycle keeps repeating..you get the idea.

2.Hibernation Issue: EVERY time I close the lid to my laptop while my computer is still running normally, I find my desktop literally split in half upon re-opening the lid.  I will try and post an image of this as soon as possible, but yes, this only happens -after- I reopen the lid.

3.Random "Tiny Bars": On the very left hand side of my screen, there are always tiny little white lines that appear randomly every few seconds.  They are horizontal and, though they aren't very noticable, they are still strange and sometimes a bit annoying.  My laptop screen is fine and was running perfectly under Windows XP.  In fact, my mouse was also just fine under Windows XP, so yes, this must be a software issue..

If ANYONE could help me, I'd be eternally grateful.  I DONT want to switch back to windows or get a new computer...so please, somebody, help.  =)

---

### Post by Angelus7 on 2007-07-03
...*Bump*
Anybody??

Again, going back to the monopoly isn't something I really want to do both financially and morally (=P)

No, but seriously, whats up with this?  Is it a video driver issue?  I have a Nvidia Geforce 2 Go...

---

### Post by xthund3rh3adx on 2007-07-03
try using fiesty fawn. the latest and greatest. this way, you can get more support, and the comptibility is better.

---

### Post by Angelus7 on 2007-07-03
Yeah...but 6.06 was supposed to have long-term support...

and THAT is why i chose it...

---

### Post by w7kmc on 2007-07-03
Hi,
If your C810 has a P-III chip like mine then there is a bug in powernowd that will cause the erratic mouse  behavior...you will see errors in /var/log/kern.log crop up every few seconds...something like "cpufreq change failed" and the system locks up for a few seconds....plays havoc on audio too!

here is the fix I  found:

1. edit  /usr/share/powernowd/cpufreq-detect.sh so that on or about line 23 -26 where it reads:

   PIII_MODULE=speedstep-ich
else
   PIII_MODULE=speedstep-smi


to read like this:


   PIII_MODULE=speedstep-ich
else
   #PIII_MODULE=speedstep-smi
   PIII_MODULE=speedstep-ich

2.  REBOOT

(in other words powernowd defaults to speedstep-ich no matter what)

editing can be accomplished with:
sudo vi /usr/share/powernowd/cpufreq-detect.sh

here is the launchpad linkto the problem:
[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/24353](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/24353)
Hope this helps...
Kevin

---

### Post by Angelus7 on 2007-07-04
That seems to have done the trick...

For now.

I will post an update on how the computer runs during an extended length of time.. (Like, over an hour or something.)

But yes, I'm pretty sure it worked.  It seems to have stopped that annoying mouse lag quite nicely.  Brilliant reply...  Thank you for your knowledge and expertise..I appreciate it.

(Oh, and next time, tell people to use the "nano" command line instead of "vi"  "nano" is much more newb-friendly..as I figured out. ;))

---

### Post by Angelus7 on 2007-07-04
Oh..and yes..mine WAS the cursed P3-m version of the Dell Latitude C810.  Sucks to be me. =D

---

### Post by w7kmc on 2007-07-04
> **Angelus7 said:**
> That seems to have done the trick...


(Oh, and next time, tell people to use the "nano" command line instead of "vi"  "nano" is much more newb-friendly..as I figured out. ;))

;)  Good deal...I guess I'm just "old school"  and generally always use vi for quick editing...

Good Luck!

---

