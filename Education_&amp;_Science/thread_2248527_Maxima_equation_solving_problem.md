---
title: "Maxima equation solving problem"
date: 2014-10-15
forum: Education &amp; Science
---

### Post by sztpet on 2014-10-15
Dear forumers!

I've ran into a problem using Maxima when trying to solve a set of equations. I'd like to calculate the crossing points of two circles. The following simple example works as it should:
```
(%i1) solve([x^2+y^2=1, x^2+(y+1)^2=1],[x,y]);
(%o1) [[x=-sqrt(3)/2,y=-1/2],[x=sqrt(3)/2,y=-1/2]]
```
But when I try it with other circles like below, it gives no solution, however there clearly should be one:
```
(%i1) solve([(y-25/sqrt(2))^2+(x-25/sqrt(2))^2=25,(y+9/sqrt(2))^2+(x+9/sqrt(2))^2=1225],[x,y]);
(%o1) []
```
I copied the exact same line into wolfram alpha and it gave me the crossing points without a problem, therefore I think the problem is with Maxima (or me missing something, I've just started to use the program), but I don't know what is it.
Does anyone have any idea of what could be the problem, why Maxima isn't able to solve the mentioned set of equations?
I use it on Ubuntu 14.04, Maxima version is 5.32.1.
Thank you in advance!

Peter

---

### Post by chaaderf on 2014-10-18
It looks like you are not alone. There is a bug in the program's solver tool. See e.g. [http://sourceforge.net/p/maxima/bugs/2736/](http://sourceforge.net/p/maxima/bugs/2736/) 

There are also some other nasty bugs in maxima that make it nearly unusable in my linux system. Fortunately, the most unpleasant bugs are in wxMaxima and not in the terminal version.

---

### Post by sztpet on 2014-10-19
Thanks chaaderf for the answer! I'd tried to google this problem before I made the forum post but somehow hadn't found this bug report page which you linked. There are some possible solutions/workarounds there, so thanks again!

---

