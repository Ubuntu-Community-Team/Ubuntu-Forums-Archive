---
title: "Hard Drive Benchmark Application"
date: 2006-04-03
forum: Desktop Environments
---

### Post by OPaul on 2006-04-03
Is there a program, similar to HD Tach for Windows, that will benchmark the random access time, burst speed and average read speed for hard drives?

---

### Post by AmboyGuy on 2006-04-03
> Hard drive bottleneck testing benchmark suite.
It is called Bonnie++ because it was based on the Bonnie program.  This
program also tests performance with creating large numbers of files.
Now includes zcav raw-read test program.  A modern hard drive will have more
sectors in the outer tracks because they are longer.  The hard drive will
have a number (often more than 8 ) of zones where each zone has the same
number of sectors (due to the need for an integral number of sectors per
track).  This program allows you to determine the levels of performance
provided by different zones and store them in a convenient format for gnuplot. 
Synaptic package manager > Search "bonnie" or it's in Sections under Utilities

---

