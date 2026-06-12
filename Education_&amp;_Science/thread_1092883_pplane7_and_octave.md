---
title: "pplane7 and octave????"
date: 2009-03-10
forum: Education &amp; Science
---

### Post by ntrgc89 on 2009-03-10
I have a pretty obscure question that I really need answered.

Is it possible to use pplane7 with octave/qtoctave? pplane7 is a matlab script (a google search returns it as the first result) that's really really good for plotting systems of differential equations..... and I need it to do my homework. 

Or otherwise, is there something in octave which could perform the same function? Thanks!!!!

---

### Post by jpkotta on 2009-03-14
I glanced at the script.  It has a bunch of GUI stuff that doesn't exist in Octave.  However, it could probably be ported if someone rewrote those functions with a text-mode equivalent, or even better used some real GUI and hooked it into Octave.

Have you checked octave-forge?  They have some diff eq packages.  All octave-forge packages should be in the Ubuntu repositories if you're using 8.10 or later.

---

