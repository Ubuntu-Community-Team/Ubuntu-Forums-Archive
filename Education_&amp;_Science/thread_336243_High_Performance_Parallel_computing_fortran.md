---
title: "High Performance Parallel computing: fortran"
date: 2007-01-11
forum: Education &amp; Science
---

### Post by neoflight on 2007-01-11
any of you guys familiar with high performance computing using Fortran 90/95?

where can I find some nice tutorial (simple ones to understand the basics and beyond) on using Fortran for parallel computing? My school provides excellent cluster facilities with inter Fortran compiler installed.

I know how to write a code in Fortran. but i don't know how to tell the compiler to do parallel processing. 

A course in Evolutionary Algorithm requires to have knowledge of this stuff...

any links, suggestions are welcome. thanks.

---

### Post by junglepeanut on 2007-01-11
Volume 2 of Numerical Recipes in Fortran

I believe a lot of it is online, I am still reading through Vol 1 so I have not read much of Vol 2 yet, except that you can use Vol 2 with out having read Vol 1.

---

### Post by kleeman on 2007-01-12
Hooray Fortran!

Here are a set of tutorials from the Maui HPC which might be useful:

[http://www.mhpcc.edu/training/tutorials/](http://www.mhpcc.edu/training/tutorials/)

Another good source of Fortran info:

[http://www.fortran.com/fortran/](http://www.fortran.com/fortran/)

---

### Post by neoflight on 2007-01-13
> **kleeman said:**
> Hooray Fortran!

Here are a set of tutorials from the Maui HPC which might be useful:

[http://www.mhpcc.edu/training/tutorials/](http://www.mhpcc.edu/training/tutorials/)

Another good source of Fortran info:

[http://www.fortran.com/fortran/](http://www.fortran.com/fortran/)

yea...i am getting the feel of it now...much user friendly than c++ "for me"....

i am planning to use python to get the ui for fortran....lets see...thanks agian

---

### Post by jeremytaylor on 2007-01-16
Just a  small point to add to the discussion. When you say "tell the compiler to do parallel processing" you have a number of options. Most compilers have some sort of auto parallelizing option... these are generally a waste of time and effort. Then you have a choice that depends on your architecture. If you have a nice chunky shared memory machine then you can use OPENMP which is incredibly easy and involves inserting a few compiler directives into your code whenever you want to make regions or loops run on multiple processors. On the other hand if you are using a cluster or machines you are probably stuck with MPI which can be somewhat nightmarish to use and or debug. If you're using the Intel compilers then they have a new feature called clusterOPENMP which can generate code for distributed memory architectures using OPENMP directives, I've not tried it but it sounds promising.

This book [http://www.amazon.co.uk/Parallel-Programming-OpenMP-Rohit-Chandra/dp/1558606718/sr=8-1/qid=1168949752/ref=sr_1_1/203-7965710-0247933?ie=UTF8&s=books](http://www.amazon.co.uk/Parallel-Programming-OpenMP-Rohit-Chandra/dp/1558606718/sr=8-1/qid=1168949752/ref=sr_1_1/203-7965710-0247933?ie=UTF8&s=books)
is pretty good even though the examples are in fortran 77. 

Jeremy

---

### Post by neoflight on 2007-01-16
> **jeremytaylor said:**
> Just a  small point to add to the discussion. When you say "tell the compiler to do parallel processing" you have a number of options. Most compilers have some sort of auto parallelizing option... these are generally a waste of time and effort. Then you have a choice that depends on your architecture. If you have a nice chunky shared memory machine then you can use OPENMP which is incredibly easy and involves inserting a few compiler directives into your code whenever you want to make regions or loops run on multiple processors. On the other hand if you are using a cluster or machines you are probably stuck with MPI which can be somewhat nightmarish to use and or debug. If you're using the Intel compilers then they have a new feature called clusterOPENMP which can generate code for distributed memory architectures using OPENMP directives, I've not tried it but it sounds promising.

This book [http://www.amazon.co.uk/Parallel-Programming-OpenMP-Rohit-Chandra/dp/1558606718/sr=8-1/qid=1168949752/ref=sr_1_1/203-7965710-0247933?ie=UTF8&s=books](http://www.amazon.co.uk/Parallel-Programming-OpenMP-Rohit-Chandra/dp/1558606718/sr=8-1/qid=1168949752/ref=sr_1_1/203-7965710-0247933?ie=UTF8&s=books)
is pretty good even though the examples are in fortran 77. 

Jeremy

thank you for the input. i shall look into that book. The syntax for 77 is a bit weired for me as i started with 90/95...

is there any pdf book on that.... thanks

---

### Post by mrphd on 2007-01-17
You could also look at this:

[http://www.openmp.org/presentations/miguel/F95_OpenMPv1_v2.pdf](http://www.openmp.org/presentations/miguel/F95_OpenMPv1_v2.pdf)

---

### Post by jeremytaylor on 2007-01-17
I don't know of a pdf version of that book. A google search for openmp reveals half a dozen tutorials that would get you started. Note that it doesn't work on clusters (well maybe the clusteropenmp does but I haven't seen any good tutorials on that) so it may be a waste of your time. MPI is harder to code but will work on a cluster.
jeremy

---

### Post by harishg on 2007-01-19
> **neoflight said:**
> any of you guys familiar with high performance computing using Fortran 90/95?

where can I find some nice tutorial (simple ones to understand the basics and beyond) on using Fortran for parallel computing? My school provides excellent cluster facilities with inter Fortran compiler installed.

I know how to write a code in Fortran. but i don't know how to tell the compiler to do parallel processing. 

A course in Evolutionary Algorithm requires to have knowledge of this stuff...

any links, suggestions are welcome. thanks.

Do you have intel fortran compiler on the machine.Intel fortran compiler has automatic parallelisation option.

ifort -o out -parallel <filename> does it all.

---

### Post by jeremytaylor on 2007-01-19
The automatic parallelization options do almost nothing as they tend to be very cautious. At best they will split up a few do loops. They will also only produce code for shared memory architectures so are no use if you're using a cluster.
Jeremy

---

