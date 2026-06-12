---
title: "Cpu running very hot! Please help!"
date: 2009-04-27
forum: General Help
---

### Post by planegenius on 2009-04-27
Today I noticed my laptop was feeling very hot.  I already had set up the sensors package, but didn't really know how to view my CPU temps.  After looking around, reading about CPU temps and how to view them, I got good news and bad news.  The good news is i can know see my CPU temp.  Bad news, it was at 90 degrees and I can't get it lower than 80.  Now, I did my homework, and can say this much-

- I already have a cooling pad
- My fans are clean, they worked just fine in XP
- I WILL NOT flash my BIOS! I'm not that experienced at all!

I did notice something.  As I hear my desktop fan turn on and off, I now realize that my laptops fan stays on always at one speed, doesn't ever seem to 'rev up'.  This does not seem normal.  I have read something about the proper signals not being sent to the fan, but how do I fix that?

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Celeron(R) M processor         1.40GHz
stepping	: 8
cpu MHz		: 1396.231
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no


acpitz-virtual-0
Adapter: Virtual device
temp1:       +83.0°C  (crit = +110.0°C)


PLEASE HELP ME OUT! I don't want my CPU to fry...

Thanks

pg

---

### Post by Arup on 2009-04-27
Check your system with system monitor for CPU load, is it around 100%, find the app thats causing it, kill it and see if that goes away. For CPU load and temp monitoring, install Gkrellm which gives you all the read out in one compact window.

---

### Post by planegenius on 2009-04-28
nope, right now with firefox the CPU load is 20-40%.  Other than that, nothing is using up my CPU, and right now its at 90 degrees on the cooling pad!:confused:

I installed gkrellm, but it doesn't seem to give me CPU temps or fan speeds.

---

### Post by ushills on 2009-04-28
see if there is a way to check to temp in bios, usually there is a system monitor. A lot of the status bar temp monitors are miscalibrated and report incorrect temp.  suggest you try a diffrent monitor app to get correct temp reported.

---

### Post by dE_logics on 2009-04-28
See if you have any utility to control the fan speed...if you did not find any, goto the bios and see if there's anyway by which a software cannot have control over the fan speed.

---

