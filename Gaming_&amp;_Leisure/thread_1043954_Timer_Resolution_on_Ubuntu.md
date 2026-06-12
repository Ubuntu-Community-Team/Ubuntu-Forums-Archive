---
title: "Timer Resolution on Ubuntu"
date: 2009-01-19
forum: Gaming &amp; Leisure
---

### Post by pha3z on 2009-01-19
can anyone tell me what resolution the timer has in the ubuntu kernel?  I'm not referring to multi-tasking resolution (as in pre-emptive switching between applications).  I'm actually referring to the system timer which is used by games to do all their computation in real-time.

i seem to have trouble finding any information that is not about the multi-tasking management.  Are the two actually directly connected?

---

### Post by curvedinfinity on 2009-01-19
times() is in 1/100ths of a second (that's the same resolution as GetTickCount() in windows, though windows returns the value in milliseconds). Both linux and windows have access to more precise timers based on the processor's clock.

---

### Post by crazyfuturamanoob on 2009-01-19
Shouldn't this be in programming talk section?

Just wanted to post something. :D

---

