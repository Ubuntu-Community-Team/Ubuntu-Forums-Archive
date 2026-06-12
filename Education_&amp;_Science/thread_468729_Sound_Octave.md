---
title: "Sound Octave"
date: 2007-06-09
forum: Education &amp; Science
---

### Post by Richard_L on 2007-06-09
Hello, I do not get any sound in Octave. I'm trying to listen to a vector.

rl@rl:~$ octave -v
GNU Octave, version 2.9.9 (x86_64-pc-linux-gnu).

*********************************************************
octave:15> n = 0:8191;
octave:16> f = 1 / 8
f =  0.12500
octave:17> x = cos (2 * pi * f * n);
octave:18> sound (x);
sox: Failed reading -: Sun/NeXT header size too small.
warning: broken pipe -- some output may be lost
octave:19> playaudio (x);
octave:20> 
*********************************************************

playaudio () dosen't complain, but no sound on my computer.

Any sugestions?

//Richard

---

### Post by Richard_L on 2007-06-10
With some amplifying can I now hear the signal, but weak.

octave:8> playaudio (200 * x)

---

