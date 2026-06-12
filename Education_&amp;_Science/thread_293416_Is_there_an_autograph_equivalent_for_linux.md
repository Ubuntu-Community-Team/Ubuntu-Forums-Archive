---
title: "Is there an autograph equivalent for linux?"
date: 2006-11-05
forum: Education &amp; Science
---

### Post by viciouslime on 2006-11-05
There is an excellent windows program called autograph but it doesn't play nicely with wine. Does anyone know of an equivalent in Linux?

For more info check out :[http://www.autograph-maths.com/]("http://www.autograph-maths.com/")

Also is there a program that can do something like this website can: [http://integrals.wolfram.com/index.jsp]("http://integrals.wolfram.com/index.jsp")

It would be nice to have an offline version.

---

### Post by Steveire on 2006-11-05
```

sudo aptitude install yacas

```
```

In> Integrate(x,a,b)Sin(x)
Out> Cos(a)-Cos(b)

```
I think that's what you want.

---

### Post by tpg on 2006-11-05
You can try gnuplot for plotting graphs - it's command line, but not too hard to learn! I use maxima for algebra, it has several good interfaces (such as wxMaxima). However, I don't know of anything with all the same tools as autograph.

---

