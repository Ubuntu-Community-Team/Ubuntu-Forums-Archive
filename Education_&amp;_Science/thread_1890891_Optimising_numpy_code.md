---
title: "Optimising numpy code"
date: 2011-12-04
forum: Education &amp; Science
---

### Post by Glenn Jones on 2011-12-04
Hey 

Not sure if this question should be in the programming or science sections. My question is about parallelising code and the most efficient way of doing this. 

The code is mostly written in python using the numpy and scipy libraries. The bulk of the processing being done by a fortran code complied using f2py (i.e., a python wrapper around the fortran code). The processing of a single datapoint takes ~ 20 s but the real issue is that I have over 5000 of these data points to process racking up a fairly substantial runtime of over a day.

I have a multi-core machine and the question is what is the best way to optimise this process? The two which have come to mind is using MPI to optimise the fortran code as its just a simple grid search and is a scalable process. The other method I thought was maybe using a job que to farm the process of each data point to each processor. I have no experience of implementing MPI in fortran and especially using f2py. I have some experience in using qsub job que but I've never set it up on my machine before. What are peoples thoughts on the problem and what would be the easiest way to improving efficiency?

Cheers

G

---

### Post by Glenn Jones on 2011-12-05
Ok so I've found some resources on using openMP to thread the fortran code but I'm having some difficulty importing the python module. After compiling using the following command 

```
f2py -c -m tvd tvd.f90 --f90flags="-fopenmp -lgomp" -lgomp --fcompiler=gfortran
```

The code appears to compile ok but when I try and import the module into python I get the following error

```
from tvd import tvd

Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ImportError: ./tvd.so: undefined symbol: doy_


```

Does anyone have any suggestions as to what the problem is and potentially how to fix it?

Cheers

G

---

### Post by ssam on 2011-12-07
openMP is much easier to use, but it only works on a single machine, whereas MPI works across a cluster of machines.

I am using openMP in C code with f2py. I compile with:
```
CFLAGS="-std=c99 -march=native -g0 -O3 -fopenmp -Wall -lm" f2py bunchstatalg.pyf bunchstatalg.c -c -lm --verbose
```

so does your code work fine (only single threaded) when you remove the -fopenmp flag?

Also if your datapoints can be calculated individually then you should probably just start lots of single threaded processes, each on a subset of the datapoints.

---

