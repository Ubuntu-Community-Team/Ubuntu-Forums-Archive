---
title: "Ocp"
date: 2010-05-18
forum: Education &amp; Science
---

### Post by Directive 4 on 2010-05-18
ocp


open caustic project (GPL)

**directive 1-**

create computer generated Euclidean space (~valid for lensing halo objects)with observer(us), lens(star with planet) and source.

model lens deformation of the space, light rays originate at the source and travel through geodesics to the lens plane and then to the observer plane (a hypothetical screen at the observer's position) where the resulting caustic can be viewed. 
[B]
directive 2-[/B]

update 1 to include Mathematics of space time. 

[B]directive 3-
[/B] 
update 2 to to include cosmological expansion and GR.

**directive 4-**

*(Classified)*


so i guess it's like a ray tracing program but with lots more fun maths.

does anyone know where one would start on such a mission, 

what programme languages would be useful, 

any open source projects i could fork:P

regards.



[http://en.wikipedia.org/wiki/Caustic_%28optics%29]("http://en.wikipedia.org/wiki/Caustic_%28optics%29")

---

### Post by radioboy on 2010-05-20
I think it depends a lot on your pretensions of time of development, portability, execution time, possible future necessities for parallelization, etc.

Even nowadays Fortran is still used for these kind of things. As favourable points you have a solid, well tested and extremely fast platform (I'm thinking of Fortran 77, 90, 95). 
On the downside, the code can get a bit complicated to manage if it gets too large.
Still, being primarily used for scientific/engineering production, you will find lots of good libraries to link to. You might need something good to work with tensors, for instance.
Another possibility is C or C++. Check also the Boost++ library.
Check also the libraries LAPACK, BLAS and ATLAS.

I would disregard Java despite the good portability, for being not so good for these kind of numerical work, but I might be wrong here.

For fast coding, with relatively easy portability (you will still have to treat cases if you want it to be used in other OSs) I would suggest Python, but the speed might not be so great.
But then you can mix code and wrap C or Fortran code with Python, taking the most computationally expensive calculations outside. For that, you can check for example
[http://www.scipy.org/PerformancePython](http://www.scipy.org/PerformancePython)
[http://fortrancython.wordpress.com/](http://fortrancython.wordpress.com/)

However, still check this:
[http://code.google.com/p/pytensor/](http://code.google.com/p/pytensor/)

Be aware of the changes in Python in the transition 2.7.x -> 3.x!
For Python check: Numpy, Scipy, Matplotlib, VTK, Maya Vi, ipython and other libraries.

If the calculations are not going to be too expensive, you might gain in having a clean, easily maintanble code and reasonable good performance.

In any case, I think you could start prototyping in Python.



No... it's not that I am a fan of Python...  :rolleyes:

---

