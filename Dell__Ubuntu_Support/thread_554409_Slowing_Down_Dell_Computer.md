---
title: "Slowing Down Dell Computer"
date: 2007-09-18
forum: Dell  Ubuntu Support
---

### Post by jamiehendrich on 2007-09-18
  Could someone please tell me if there is any way to slow down a Dell desktop with no CPU scaling?  

It has a 3+ Mghz processor -- if that's the right word, "processor" but I am working with dosemu and it is too fast for running my old software.  It needs to be 1.8 - 2 Mghz.  

A.  Is there software compatible with Edgy that I could purchase?

B.  I was advised to type:  sudo gedit /etc/dosemu/dosemu.conf and remove the hashmark and change the cpu speed to 66.0.  Still too fast.  It has not slowed down at all.  Also, it was suggested that I remove the hashmark and change the hogthreshold to "0."  Still no change.

Any ideas?    Thank you so much.

Jamie

---

### Post by neptho on 2007-09-19
If you really want to get it slower, don't use dosemu.  Use Bochs with [a FreeDOS image](http://www.oldskool.org/pc/throttle/DOS); install [Throttle](http://www.oldskool.org/pc/throttle/DOS), or [Mo'Slo](http://www.hpaa.com/moslo/) on it.

This really isn't a Dell question; it'd make much more sense in the 'General Questions' area.  :)

---

### Post by jamiehendrich on 2007-09-19
Actually it's a "computer purchaser" problem.  I said Mghz in the above message.  Actually it's a  3+ Ghz, not mghz.    I will try to work with it further.  I was informed that  slo-mo or mo-slo will not work with my setup.     I may be forced to purchase a new computer but a slower one.    Thank you for responding.  

Jamie

PS  Sorry I was in the wrong place.  I placed messages everywhere, even in the general questions, out of sheer desperation!

---

### Post by phr0ze on 2007-09-25
> **jamiehendrich said:**
> 
PS  Sorry I was in the wrong place.  I placed messages everywhere, even in the general questions, out of sheer desperation!

FYI: On most forums it is against the rules to post in multiple categories.

---

