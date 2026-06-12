---
title: "[SOLVED] Inspiron 530 fan won't shut up!"
date: 2008-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eapache on 2008-06-23
I have a brand new inspiron 530, and the fan runs all the time regardless of the cpu tempurature etc.

This isn't listed under the known issues that I could find, but there must surely be a workaround of some sort?

---

### Post by danbodoh on 2008-06-23
I played with the sensors module and fancontrol for a while, but couldn't improve it.  The speed of the power supply fan is not controllable.  The cpu fan has a min speed; it won't shut off.  Controlling the case fan didn't help with noise much.

That being said, the 530 is a much quieter than my previous no-name box.

Dan Bodoh

---

### Post by eapache on 2008-06-24
At min speed (in Vista) it's fairly quite and quite bearable. In Ubuntu however, it roars the whole time at max (the way it does for a few seconds when you first turn it on). It seems that the kernel update from .17 to .19 fixed it though.

---

