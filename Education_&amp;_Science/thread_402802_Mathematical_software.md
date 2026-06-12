---
title: "Mathematical software"
date: 2007-04-06
forum: Education &amp; Science
---

### Post by Zdravko on 2007-04-06
Hi! I search for a nice and comprehensive Mathematical software for Feisty. What can you recommend me?
I need matrices, integrals, functions plotting.

---

### Post by akniss on 2007-04-06
**Scilab**
[http://www.scilab.org/](http://www.scilab.org/)
```
sudo aptitude install scilab
```
Some users have had issues with text showing up only in Hindi when installing scilab from the Ubuntu repos. This is probably fixed by now, but if not, there is a binary version available on the scilab website. Just unpack it and read the README_Unix file.

**Maxima**
[http://maxima.sourceforge.net/](http://maxima.sourceforge.net/)
```
sudo aptitude install maxima
```

**Octave**
[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)
```
sudo aptitude install octave
```

---

### Post by witten on 2007-04-08
Hi, 

If you want a really good software for all symbolic, numeric and plotting needs you have, try Mathematica...it's not free but damn good. I use it all the times.

Steeve
E. Witten - Master of superstring theory

---

### Post by rufius on 2007-04-09
I would also mention R if you're handling matrices. 
```
apt-get install r-base
```

---

### Post by tyreth on 2007-04-12
As a non-free solution, what do you guys think of Matlab?

---

### Post by Zdravko on 2007-04-12
We think of it as a non-free solution! :(

---

### Post by NiRaDo on 2007-04-12
> **akniss said:**
> **Scilab**
**Maxima**
[http://maxima.sourceforge.net/](http://maxima.sourceforge.net/)
```
sudo aptitude install maxima
```


I give advice to install **wx**maxima who is based to maxima, but it can be viewed thanks to gtk : it has a GUI. So it's easier than maxima to insert matrices, integrals or functions plotting.

Even if I like Terminal, I think it's more ergonomic than a black screen to do this wear.

---

### Post by in_flu_ence on 2007-04-12
Another non-free product is mupad. It looks very much like mathematica and seem to run pretty well in ubuntu. I tried the trial version.

---

### Post by UltraMathMan on 2007-05-01
I'd second wxmaxima, I'm very happy with it - it has a similar command syntax to Maple (another non-free option).

-Hope this helps :)

---

### Post by orodoni_le on 2007-05-02
Is there anything similar to Mathcad? :confused: 
Similar on the command syntax, or even the GUI

---

### Post by zgornel on 2007-05-03
By far the most advanced of ALL is Matlab. It is not free :(

---

### Post by Zdravko on 2007-05-03
I am searching only for FREE solutions.

---

### Post by outer_space on 2007-05-06
I havnt tried wxmaxima but I tried scilab and its comparable to matlab.  I took a matlab image processing course and had no problem using scilab instead of matlab.

What makes wxmaxima  better than scilab?

---

### Post by Uodnelome on 2007-05-06
> **rufius said:**
> I would also mention R if you're handling matrices. 
```
apt-get install r-base
```

Interesting -- my introductory statistics program only used R for its graph plotting, and standard deviation functions.  It's also pretty robust there, with all sorts of commands to calculate percentages based on the standard deviation given a normal distribution -- the trick is learning all of the commands first.

It's kind of daunting, but is pretty powerful once you know how to use it.

[http://www.r-project.org/](http://www.r-project.org/)
...should anyone want to read the project's website.

---

### Post by engla on 2007-05-07
> **outer_space said:**
> I havnt tried wxmaxima but I tried scilab and its comparable to matlab.  I took a matlab image processing course and had no problem using scilab instead of matlab.

What makes wxmaxima  better than scilab?

You shouldn't say better. They are very different in many ways. Scilab is probably tons better for say, image processing. Maxima is mostly about algebraic manipulations (even if it can do numeric operations as well with high precision). The allegory is that scilab is like matlab, and maxima is like maple.

---

### Post by euler_fan on 2007-05-08
> **Uodnelome said:**
> Interesting -- my introductory statistics program only used R for its graph plotting, and standard deviation functions.  It's also pretty robust there, with all sorts of commands to calculate percentages based on the standard deviation given a normal distribution -- the trick is learning all of the commands first.

It's kind of daunting, but is pretty powerful once you know how to use it.

[http://www.r-project.org/](http://www.r-project.org/)
...should anyone want to read the project's website.

I taught myself enough R to get some stuff done, and yeah, it does take a fair bit of time to get rolling but I highly recommend it. It seems to work really well and from what I have read many of the numerical methods actually use FORTRAN routines on the backside, at least for most of the stuff in the core and the more serious packages.

The introduction to R on the project's web page is quite good.

---

