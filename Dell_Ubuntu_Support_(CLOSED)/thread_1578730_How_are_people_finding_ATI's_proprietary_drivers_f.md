---
title: "How are people finding ATI's proprietary drivers for Dell Studio GPUs these days?"
date: 2010-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by soulspit on 2010-09-20
Hi everyone,

I have a Dell Studio 17 (specifically the 1747), with an ATI Radeon HD 4650.  Right now I'm using the open-source drivers, but I've noticed that the fan runs way more than it does on Windows 7, my laptop gets quite a lot hotter, and the battery life is about a third shorter, and I was thinking that the proprietary drivers might help with some of these things (and maybe let me access some temperature sensors? I can't get a single one).

In researching this all, I found people having a lot of difficulty with the fglrx drivers and the AMD's own proprietary binaries, but all of the posts I found were from 2008 and 2009.  I haven't really been able to find anything out there that was particularly authoritative on the pros and cons of each driver... So, I was wondering if anyone with any current experience with these drivers on any Dell Studio computer could share their wisdom with me.  Should I install them?  Might they fix my problems?  Will it brick my laptop?  And, should I go with the older ones in the Ubuntu repositories or download the newest binaries (currently version 10.9) from the AMD website?

Any thoughts would be appreciated.  Thanks!

---

### Post by anjilslaire on 2010-09-21
I have a XPS 7100 desktop with a Radeon 5450, and the propriety drivers work great.

---

### Post by soulspit on 2010-09-22
Bump!  That's good to hear, but I was hoping to see how many people report the same, and if anyone has had deal-breaker problems like the ones that seemed to have existed a year or two ago.  Thanks again!

---

### Post by soulspit on 2010-09-24
For what it's worth, I installed fglrx (from kde's restricted hardware drivers tool) and the display looks good, and the temperature is down, and I can see the temperature by running
```
aticonfig --adapter=0 --od-gettemperature
```though I can't get lm-sensors to pick this up.  But the splash screen is 640x480/looks ugly, and compositing stopped working, and [I can't get compiz to work]("http://ubuntuforums.org/showthread.php?t=1580840"). So, all around sort of a lateral move rather than a step forward.  Just in case anyone was interested...

---

