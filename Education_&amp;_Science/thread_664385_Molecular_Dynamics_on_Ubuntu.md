---
title: "Molecular Dynamics on Ubuntu????"
date: 2008-01-11
forum: Education &amp; Science
---

### Post by bioxg on 2008-01-11
[SIZE="3"]:)Hi, everyone!
Anybody use Ubuntu to do molecular dynamics(MD)?
And Use NAMD?
Is it good?[/SIZE]:):)

---

### Post by i2000s on 2008-01-11
no&#65292;I  haven't.
But I am interested in this topic, Molecular Dynamics .I am majoring in physics.
Would you mind do me a favor to introduce the soft of NAMD or other else that can be used in this field?
Many Thanks~

---

### Post by bioxg on 2008-01-12
> no&#65292;I haven't.
But I am interested in this topic, Molecular Dynamics .I am majoring in physics.
Would you mind do me a favor to introduce the soft of NAMD or other else that can be used in this field?
Many Thanks~

Ok. NAMD is a parallel molecular dynamics code designed for high-performance simulation of large biomolecular systems. Based on Charm++ parallel objects, NAMD scales to hundreds of processors on high-end parallel platforms and tens of processors on commodity clusters using gigabit ethernet. NAMD uses the popular molecular graphics program VMD for simulation setup and trajectory analysis, but is also file-compatible with AMBER, CHARMM, and X-PLOR. NAMD is distributed free of charge with source code. You can build NAMD yourself or download binaries for a wide variety of platforms. Our tutorials show you how to use NAMD and VMD for biomolecular modeling.

AND THIS IS IT'S WEBSITE
[http://www.ks.uiuc.edu/Research/namd/]("http://www.ks.uiuc.edu/Research/namd/")

---

### Post by bioxg on 2008-01-12
> I am majoring in physics.
my major is biophysics & condense matter physics
HAVE A TRY! FRIENDS

---

### Post by mrkilgoretrout on 2008-01-13
MD is a part of my research, but I write my own programs.  I suggest you do the same if you really want to understand what is going on.

---

### Post by benhall on 2008-01-23
Another good alternative if you have limited resources is Gromacs. It is available in the repositories (its under the GPL), and is much faster than NAMD for small numbers of processors. Benchmarks performed here show that for a membrane protein system, Gromacs is ~10x faster than NAMD on a single processor, and despite the better scaling of NAMD you still need 72 processors before NAMD starts outperforming Gromacs.

I don't think that writing your own MD code is necessary unless you really want to develop it; there are several highly optimised code bases out there (including NAMD, Gromacs, Charmm, and others) which will be faster and have passed intense peer review. If you just want a simulation of a biomolecule you are better reading the documentation and using one of these. Alternatively, if you want to understand the details of how the code works, I believe that there is a program called tinker which is very readable/hackable.

---

### Post by Tharmas on 2008-02-07
Well, you also have [Tinker]("http://dasher.wustl.edu/tinker/") as an alternative.

---

### Post by DaRQsiDe on 2009-06-16
Hey,

I use AMBER, pmemd module parallelizes better till 512 cpu's than NAMD. If you are interested in AMBER, see ambermd.org.

One thing is... it's not free. If you want something free, definitely go with NAMD.

If you need a comparison of different force fields (since the heart of the MD is the force field - potential energy function) look at the Manuel Orozco paper at 2007 (if my memory serves me right) for a comparison of different mainstream force fields on biomolecules.

For writing your own programs, I think the best start will be to simulate two atoms on a harmonic potential well - either using MD (Verlet algoritm) or MC (Metropolis Monte Carlo)

---

### Post by Morpholinux on 2010-06-19
I am also interested at molecular dynamics (MD). I use (or learning to) NAMD, CHARMM, and VMD.
All work well with Ubuntu 10.04..(at least I do not have not problems).
CHARMM's documentation is a bit ugly and outdated. There are a few tutorials. 
VMD and NAMD on the other hand have very good tutorials and doc. 
Haven't tried GROMACS...but I'll do it.
Somebody knows about a MD data repository. I found something called PI found ([http://www.p-found.org/)...but](http://www.p-found.org/)...but) currently new user registration is not available.... ..
Something like that will be very useful.

well ..
that's all for the moment.

ps..I google "manuel orozco force field comparison" and ..nothing....

---

