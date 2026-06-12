---
title: "Maple 3D"
date: 2010-11-21
forum: Education &amp; Science
---

### Post by piivo on 2010-11-21
Ok hello everyone and thank you in advance.
I have 2-3 difficulties in a maple plotting.
I'm trying to plot two fairly easy surfaces in maple 3d. 
What I want is:
3 standard axis, x,y,z with y vertical and z coming out of the screen(obviously you can turn it and stuff.)

Two surfaces:
On with y = (1/x), z=free;
The second with y= 2*x(1/z);
Both should be in the same System


I would have expected something like this:(This is not copyable text)
f := (x, z)->1/x;
g := (s, t)-> 2*x(1-1/z);
plots[display](plot3d([f, g], 0 .. 4, 0 .. 4, axes = boxed),
view = [0 .. 5, 0 .. 5, DEFAULT])

However, no matter how I switch around the parameters, g() stays independent of z. The other obvious solution would be something along the lines of f := y = 2*x*(1-1/z); but that doesn't work at all.

Second Problem:
Once the first bit works, I want to plot a line that represents the intersections of the two surfaces in the same graph, so I have to create surface with a restriction or something. Can't see how though.

Third Problem:
And last, this gets really tricky, I want to plot the two surfaces in discrete intervals of z, but the line in a continuous form.

If anyone can help in any part of the Solution I would be very gratefull.
I'm not maths student and I need this graph for a paper, so I'm pretty much out of my depth.
thanks 
Ivo

---

