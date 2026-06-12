---
title: "Help me with matrices"
date: 2007-03-30
forum: Education &amp; Science
---

### Post by Zdravko on 2007-03-30
Hi! I just wrote a C++ application for my course work, that calculates the determinant and the inverse of a 10x10 and a 20x20 matrix. Can you suggest me an internet application (or applet) that works with such sizes, so that I can check and compare my result?
[http://www.bluebit.gr/matrix-calculator/](http://www.bluebit.gr/matrix-calculator/) - this one allows only 12x12! :(

---

### Post by jeremytaylor on 2007-03-30
Can't think of an internet application but you could use octave... It's dead easy to use and is designed to do just such operations as matrix inversion.

Jeremy

---

### Post by Zdravko on 2007-03-30
I am using Windows now. I don't have this.
Can you help me? Then generate a matrix 20x20 of ints - use small numbers, 0, +/-1, +/-2.
Thank you in advance!

---

### Post by WW on 2007-03-30
You could use Scilab ( [http://www.scilab.org/](http://www.scilab.org/) ). They provide a Windows version.

In Scilab, you can do this:
```

-->A = floor(5*rand(5,5)-2)
 A  =
 
    2.  - 2.    2.    0.    1.  
  - 2.    1.  - 1.  - 1.    0.  
    1.    1.    0.    0.    2.  
  - 2.  - 1.    1.    0.  - 2.  
    2.    2.  - 2.  - 2.    0.  
 
-->det(A)                  
 ans  =
 
    30.  
 
-->inv(A)                  
 ans  =
 
    0.   - 0.3333333    0.    0.     0.1666667  
  - 0.4  - 0.4666667    1.    0.8    0.2333333  
    0.   - 0.3333333    1.    1.     0.1666667  
  - 0.4  - 0.4666667    0.  - 0.2  - 0.2666667  
    0.2    0.4          0.  - 0.4  - 0.2        
 
-->

```
For 20x20, change rand(5,5) to rand(20,20).

---

