---
title: "Jaunty: Constant Hard Drive Activity"
date: 2009-04-25
forum: General Help
---

### Post by spongypants23 on 2009-04-25
Having a wee bit of trouble with Jaunty here...

My hard drive is pretty much constantly active, as in making its little "I'm-working" noise, and the hard drive light flashes continuously.

This happens even if all open programs are quitted, leaving only basic things open such as AWN, padevchooser, etc etc.

This causes my system to be a little sluggish...

And I'm a little worried this heavy increase in hard drive activity will severely decrease the lifespan.

Any help?

---

### Post by reefdiver5 on 2009-04-26
my laptop developed this problem shortly after I upgraded to Jaunty, I was able to stop the light flashing by going into the system>administration>services and re-enabling mysql and restarting.  Turning it off was what caused the problem, I believe it is used by mythtv.  This [other thread]("http://ubuntuforums.org/showthread.php?t=1051875&highlight=9.04+hard+drive+light+continuously+flashing&page=3") mentions the same problem and says they solved it by finishing configuring the mysql for myth.

Thats the most i know about it and I do believe it can cause damage if it goes on to long,
good luck

---

### Post by mtbdrew on 2009-04-28
I've noticed the same thing one my system after installing 9.04

---

### Post by 99_rover on 2009-04-28
I have the same problem - found another thread which looked like it might be a solution

[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

I got the first part of this to work OK but the last section to change centisecs to 6000 would not change - or if it did it reverted after reboot

---

### Post by mtbdrew on 2009-04-29
> **99_rover said:**
> I have the same problem - found another thread which looked like it might be a solution

[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

I got the first part of this to work OK but the last section to change centisecs to 6000 would not change - or if it did it reverted after reboot

Tried all the mods listed there and still have constant hard drive activity.

---

### Post by spongypants23 on 2009-05-01
**Solved** my problem by removing Tracker.

```
sudo apt-get remove tracker
```

---

### Post by NilsE on 2009-05-01
> **spongypants23 said:**
> **Solved** my problem by removing Tracker.

```
sudo apt-get remove tracker
```
That may very well be the answer.  I noticed the same problem and found tracker running pretty steady.  It stopped after a couple of days when tracker finished it's initial indexing.

---

### Post by ajaysutton on 2009-05-01
Very nice.  Removing Tracker seems to have resolved this issue for me.

---

### Post by DavidTangye on 2009-05-01
See the launchpad bug reports [including this one]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912").

---

### Post by mtbdrew on 2009-07-09
Removing the tracker did not help. Any other ideas?

---

### Post by thijsz on 2009-08-03
do you have Mythtv running ?
i could stop the HD activity by killing the mythtv backend 
dont know why it is doing this, but it helped :)

---

