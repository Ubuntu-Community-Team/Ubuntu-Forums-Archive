---
title: "ZSNES Sound Problems"
date: 2004-12-21
forum: Gaming &amp; Leisure
---

### Post by soritong on 2004-12-21
I got ZSNES running nice and smoothly, but I can't figure out for the death of me how to get the sound work.

I've tried fiddling with the configs, yet nothing is working.

Anyone have any ideas?

---

### Post by rolfijn on 2004-12-27
Hi there,

had the same problem. Fixed it (or at least, made it work) by installing the package alsa-oss from universe. You could give it a try.

Rolf Deenen.

---

### Post by bigdee973 on 2008-08-20
u dont need to configure nothing or mess with any files just open up terminal and type in 

zsnes -ad sdl

sound should work perfect from now on when u click the zsnes link... dont use sudo for this...that will just allow sound when u run zsnes as root... type it just the way i gave it to u and sound will work everytime from now on.

---

### Post by Zinake on 2008-09-26
> **bigdee973 said:**
> u dont need to configure nothing or mess with any files just open up terminal and type in 

zsnes -ad sdl

sound should work perfect from now on when u click the zsnes link... dont use sudo for this...that will just allow sound when u run zsnes as root... type it just the way i gave it to u and sound will work everytime from now on.

Also make sure that you have your sound sampling rate @ 48000HZ.  It still sounded like crap when I had the sound at the default sampling rate.

---

### Post by williane on 2008-10-04
Confirmed. I had the same problem and this worked for me. Thanks a lot!

---

### Post by JonahRowley on 2008-10-24
I've noticed that the sound breaks if you go to fullscreen, sounding really noisy or choppy.  If you change the sample rate after you go to fullscreen, then it fixes this.  Luckily, you can enter the GUI in fullscreen to do this.  On some emulators (like Gens, which has this same problem), you can't enter the GUI in fullscreen and you're stuck with this problem.

---

### Post by mesact on 2009-05-18
I know im a few months late, but this worked for me also! :D THANX ALOT

---

