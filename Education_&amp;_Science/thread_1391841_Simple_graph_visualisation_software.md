---
title: "Simple graph visualisation software"
date: 2010-01-27
forum: Education &amp; Science
---

### Post by Nevon on 2010-01-27
About a year ago, I remember using this GTK based application for visualizing equations. It was pretty simple, all you had to do was define an equation (and possibly a variable range) and it plotted it for you. However, I can't for the life of me remember what it was called. I think the name started with G, but I'm not sure.

I've gone through the repository to try to find it, but I just can't. Does anyone have a clue as to what the program might be called?

These are the ones I have confirmed that it's not:
matlab
gnuplot
graphmonkey
octave
graphthing
qgfe

---

### Post by hubie on 2010-01-28
If there is a GTK front-end for gnuplot (is that what qgfe is?) then [that kind of thing shoudl be pretty easy]("http://t16web.lanl.gov/Kawano/gnuplot/intro/plotfunc-e.html").

If you don't mind the command line, what you want to do is pretty easy in most of the programs you list.  I can't help but give an example from my favorite quick plot program, R:

```
m <- 2.0
b <- 120.0
curve( m*x + b, from=-100, to=100)
```

In some of the other programs, such as octave, you might need to define a vector of x values first.

---

### Post by cronco on 2010-01-28
A very very simple graph plotter is lybniz for gtk, which is very basic, or kmplot for kde, which has a bit more features, but is still very easy to use.

---

### Post by Nevon on 2010-01-30
> **hubie said:**
> If you don't mind the command line, what you want to do is pretty easy in most of the programs you list.  I can't help but give an example from my favorite quick plot program, R:
It's not that I mind using the command line, but I'm looking for a specific program here. 

> **cronco said:**
> A very very simple graph plotter is lybniz for gtk, which is very basic, or kmplot for kde, which has a bit more features, but is still very easy to use.

It's neither of those. But lybniz looks almost exactly like what I'm looking for, so if I can't find it, I could probably use that instead.

---

### Post by alexfish on 2010-01-31
hi

have you looked here

[http://edu.kde.org/kalgebra/](http://edu.kde.org/kalgebra/)

[http://kalgebra.berlios.de/](http://kalgebra.berlios.de/)

---

### Post by oldfred on 2010-01-31
I plugged in equation plot in synaptic and came up with a vareity of programs.
Perhaps r-base (gnu R ) or kmplot ( which you still can run in ubuntu, it will add whatever packages it needs)

---

### Post by Sporkman on 2010-01-31
There are web-based online ones as well.

---

