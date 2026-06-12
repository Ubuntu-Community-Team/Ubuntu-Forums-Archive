---
title: "Statistical software"
date: 2006-05-15
forum: Education &amp; Science
---

### Post by nvbauer on 2006-05-15
What would be the GNU equivalent of MathCAD? My engineers are asking for MCAD, but the boss does not want to put out the dough for it. He feels that Excel would be sufficient (ha). I think this would be a great time to introduce Ubuntu to our company. 

Thanks,

Norm

---

### Post by glinsvad on 2006-05-15
Copy/paste from [http://www.redhat.com/archives/rhl-list/2005-September/msg02664.html]("http://www.redhat.com/archives/rhl-list/2005-September/msg02664.html"):
> Maxima is a version of the MIT-developed MACSYMA system, modified to run under Common LISP. It is an interactive expert system and programming environment for symbolic and numerical mathematical manipulation. Written in LISP, it allows differentiation, integration, solution of linear or polynomial equations, factoring of polynomials, expansion of functions in Laurent or Taylor series, computation of Poisson series, matrix and tensor manipulations, and two- and three-dimensional graphics.
Procedures  may  be  written using an ALGOL-like syntax, and both LISP-like functions and pattern matching facilities are provided. Files containing maxima objects may be read from and written to disk files. Pre-written maxima commands may be read from a file and executed, allowing batch-mode use.

[http://maxima.sourceforge.net/]("http://maxima.sourceforge.net/")

Sounds to me like a Maple-equivalent... which has a bunch of free clones

Anyway, Maxima is in the universe repositories
```
sudo apt-get install maxima
```

---

### Post by nvbauer on 2006-05-15
Thanks. I'm going to give it a try.

---

### Post by glinsvad on 2006-05-15
You'r welcome. Also check out [Scilab]("http://www.scilab.org/") for more CPU-intensive numerical calculations

---

### Post by thk on 2006-05-15
For statistics you want R (r-base).

---

