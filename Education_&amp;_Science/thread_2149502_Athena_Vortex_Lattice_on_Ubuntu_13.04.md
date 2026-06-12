---
title: "Athena Vortex Lattice on Ubuntu 13.04"
date: 2013-05-29
forum: Education &amp; Science
---

### Post by neosoyo on 2013-05-29
Hi Everyone! I'm trying to use the avl on my desktop running ubuntu 13.04 64bits, try several combinations of compiler and flags to make it work fine but i have no sucess..

i use the tutorial of this [thread]("http://ubuntuforums.org/showthread.php?t=1182359&highlight=avl") but i've got NaN errors when i run the session1.txt example provided by Mark Drela [here]("http://web.mit.edu/drela/Public/web/avl/session1.txt").

The program run fine until the trimming step, after set the trimming conditions for the airplane the calculation stop's at ter 1:

```

ter d(alpha)   d(beta)    d(pb/2V)   d(qc/2V)   d(rb/2V)   flap       aileron    elevator   rudder     
   1  0.521E-03  0.160E+01  0.198E-02 -0.000E+00 -0.140E+00 -0.000E+00  0.630E+00 -0.205E-01 -0.102E+01
   2        NaN        NaN        NaN        NaN        NaN        NaN        NaN        NaN        NaN
   ....
  20        NaN        NaN        NaN        NaN        NaN        NaN        NaN        NaN        NaN
 Trim convergence failed

```

i read about double precision problems on the compilation, but when i compile at single precision, the Xplot don't work at all (black screen only).

Can you guys help me to fix that?

Cheers,
Saulo Barbosa

---

