---
title: "Are free mathematical siftwares available for ubuntu 10.04LTS?"
date: 2011-12-23
forum: Education &amp; Science
---

### Post by arroy_0209 on 2011-12-23
Are free mathematical softwares capable of doing numerical solutions of differential equations, plotting etc available for Ubuntu 10.04 LTS? The software should be good for scientific applications in general. If you know any or have used any such package, please suggest.

---

### Post by dargaud on 2011-12-23
```
sudo aptitude install science-mathematics
```
will install a whole bunch of them...

---

### Post by sanderd17 on 2011-12-23
I discovered a mathematical package for Linux (it doesn't work on Windows for the moment) that is more powerfull then Maple, Mathematica and Matlab together.

[https://help.ubuntu.com/community/SAGE](https://help.ubuntu.com/community/SAGE)

It's a command line tool in the first place, but you can also start it as a web service and access it through your browser via a nice interface (although you get lesser options since you can't access your personal file system, which can be a problem like when you want to export graphs)

It's based on Python, so you can call all python functions you want for numerical analysis, and the framework itself gives access to a huge library with symbolic things (e.g. symbolic differentials, integrals, create your own algebraic structures ...).

It's advisable to read a tutorial when you start: [http://www.sagemath.org/tour.html](http://www.sagemath.org/tour.html)

BTW, I found this via Vincent Knight on Google+: [https://plus.google.com/u/0/110464871801965858778/posts](https://plus.google.com/u/0/110464871801965858778/posts)

---

