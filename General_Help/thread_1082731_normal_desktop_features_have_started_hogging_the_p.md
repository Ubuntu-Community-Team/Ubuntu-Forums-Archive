---
title: "normal desktop features have started hogging the processor"
date: 2009-02-28
forum: General Help
---

### Post by ireneshusband on 2009-02-28
At some point during the relatively recent past certain everyday desktop functions have started hogging the processor, pushing it to 100% at full throttle. Middle-clicking and scrolling the page in both Opera and Firefox does this. So does alt-tabbing to switch windows. So does the Gnome Exposé clone. When I try to use these features, things get quite slow and jittery.

I am using a Thinkpad R61i, a  64-bit machine which has one of those Intel graphics chips for which the driver cannot yet handle compositing (so that, for instance, I cannot make use of GoogleEarth while Compiz is enabled). However I had been running Ubuntu Intrepid on this box for some time before this cpu-hogging started.

I have tried to edit my xorg.conf at some point in order to work round the compositing issue, but I cannot see anything in my current xorg.conf that looks remotely like it could be causing this. But I am attaching it here just in case.

---

### Post by dbbolton on 2009-02-28
> **ireneshusband said:**
> At some point during the relatively recent past certain everyday desktop functions have started hogging the processor, pushing it to 100% at full throttle. Middle-clicking and scrolling the page in both Opera and Firefox does this. So does alt-tabbing to switch windows. So does the Gnome Exposé clone. When I try to use these features, things get quite slow and jittery.

I am using a Thinkpad R61i, a  64-bit machine which has one of those Intel graphics chips for which the driver cannot yet handle compositing (so that, for instance, I cannot make use of GoogleEarth while Compiz is enabled). However I had been running Ubuntu Intrepid on this box for some time before this cpu-hogging started.

I have tried to edit my xorg.conf at some point in order to work round the compositing issue, but I cannot see anything in my current xorg.conf that looks remotely like it could be causing this. But I am attaching it here just in case.
Try logging in to a Failsafe Gnome Session and see if this still happens

---

### Post by ireneshusband on 2009-02-28
Thanks. Good advice that is so easy to forget.

As it happened, I was having audio problems as well, so I booted into Windows just to check that it wasn't a hardware issue. The audio worked fine. When I booted back into Linux not only was the audio problem cured, but this issue with the graphics had disappeared too.

---

### Post by dbbolton on 2009-02-28
> **ireneshusband said:**
> Thanks. Good advice that is so easy to forget.

As it happened, I was having audio problems as well, so I booted into Windows just to check that it wasn't a hardware issue. The audio worked fine. When I booted back into Linux not only was the audio problem cured, but this issue with the graphics had disappeared too.
I am always disturbed when something randomly stops working, but I find myself even more disturbed when things randomly start working on their own :D

---

