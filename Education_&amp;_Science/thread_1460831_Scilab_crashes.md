---
title: "Scilab crashes"
date: 2010-04-23
forum: Education &amp; Science
---

### Post by MindSz on 2010-04-23
Hi, I'm trying to do some coherence analysis and I need to use either fft() or pspect() but every time I try one of these functions, Scilab crashes.

I'm using Scilab 5.2.1 which I got from their website. Do I need to install extra packages or am I doing something wrong?

Here's a small example of what I'm trying to do:

```
clear;
stacksize('max');
A=(sin([0:0.01:100]))*0.5;
inct = 0.01;
incf = 1 / (100 * inct) ;
segment = 1:500;
tscale = segment * inct;
xsetech([0,0,1,1/2])
plot2d(tscale,A(segment));
psA = pspect(50,100,'hn',A);
xsetech([0,1/2,1,1/2])
plot2d(tscale,psA(segment));

```

...the code may have some errors cuz I haven't had a chance to see it running yet.

Thanks!

---

