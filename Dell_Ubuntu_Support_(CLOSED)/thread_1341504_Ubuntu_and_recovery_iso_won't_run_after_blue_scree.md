---
title: "Ubuntu and recovery iso won't run after blue screen"
date: 2009-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by davedocdoodle on 2009-11-29
First, a blue screen.
I halted "physical memory dump" (oops??)
Have since tried to recover with, FAILED:
A. Recently burned SP3 XP-Pro boot disk supplied by full time computer repair man 21 yrs in biz.
B. BitDefender recovery iso
C. Kaspersky recovery iso
D. Ubuntu on CD
E. Ubuntu on flash drive
all above failed to boot even when I used boot menu numerous times to make CD or flash first to load. 

Ran Dell's utility to scan HDDs._ Read test did NOT run, but no errors_. Everything else passed. CD drive passed.

Am at limit of my knowledge. Consider myself* below *intermediate knowledge. Now what, please? (Thank you!!)

---

### Post by mikewhatever on 2009-11-30
That could easily be a hardware problem, perhaps a faulty memory stick. I would have recommended running memtest, but since that's not possible, try a general internal check, look at the motherboard capacitors, try taking out one of the RAM sticks, that is, if there are more then one.

---

### Post by davedocdoodle on 2009-11-30
Mikewhat,

All the hardware was working just fine. The bluesreen occured the instant I closed a web browser (Firefox) tab from a site I felt was misbehaving in some way. I think it was.

If not hardware, then???

---

### Post by mikewhatever on 2009-11-30
Do you get any error when booting from a cd?

---

### Post by davedocdoodle on 2009-11-30
Mikewhat,

no error loading cd or flash drive, I just can't boot from either one even when I force the computer to boot from them. Can't boot from anything. 

It just tries to start the XP-Pro or gives a list of stuff when I try boot from command prompt, last string ends in
**multi(0)disk(0)rdisk(0)partition(2)\WINDOWS\system32\DRIVERS\agp440.sys**

---

### Post by DGortze380 on 2009-11-30
> **davedocdoodle said:**
> First, a blue screen.
I halted "physical memory dump" (oops??)

That's your clue right there.
You have a memory problem.

Run Memtest is you can get it to boot.

If you have more than 1 DIMM, try removing 1 and booting again.
Remove another, boot again. Etc... to identify which stick is bad.

---

### Post by davedocdoodle on 2009-12-05
DGortze,

I do not know the steps to accomplish what you suggest nor know what DIMM1 is.

---

### Post by DGortze380 on 2009-12-05
> **davedocdoodle said:**
> DGortze,

I do not know the steps to accomplish what you suggest nor know what DIMM1 is.

[http://www.memtest86.com/](http://www.memtest86.com/)

DIMM is a stick of RAM (memory)

---

### Post by em3raldxiii on 2009-12-05
I second the opinion about faulty RAM.  It is very easy to pull one ram stick, unless there are a lot of chords and other junk in the way.  Most computers nowadays have 2 of them running in Dual mode (not all), so you might be in luck.  Open the side, close to the huge CPU heat sink should be two vertical cards that are about 4 ro 5 inches long and about 1 inch wide.  Some have heat sinks strapped to them, but if not it should be easy to press the little clips on both ends of one of the sticks and carefully pull it out.  Then try booting.  Then, noting the boot result, switch the sticks in the same socket.  It's a good idea to try to get the "first" socket in the row (some motherboards are configured to only use that slot when it only has 1 stick).

Just be careful not to jab anything or pull out chords.  Generally, this is a painless activity.

---

### Post by em3raldxiii on 2009-12-05
This might help:

[http://www.youtube.com/watch?v=SsXNT6fnHmM&feature=fvw](http://www.youtube.com/watch?v=SsXNT6fnHmM&feature=fvw)

---

