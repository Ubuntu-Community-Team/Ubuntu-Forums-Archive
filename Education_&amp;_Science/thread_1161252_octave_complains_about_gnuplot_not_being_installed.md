---
title: "octave complains about gnuplot not being installed"
date: 2009-05-16
forum: Education &amp; Science
---

### Post by petersk on 2009-05-16
I get this error when trying the example at:

  octave:1> x = -2:0.1:2;
  octave:2> [xx,yy] = meshgrid(x,x);
  octave:3> z = sin(xx.^2-yy.^2);
  octave:4> mesh(x,x,z);


[http://math.jacobs-university.de/oliver/teaching/iub/resources/octave/octave-intro/octave-intro.html](http://math.jacobs-university.de/oliver/teaching/iub/resources/octave/octave-intro/octave-intro.html)

error: you must have gnuplot installed to display graphics; if you have gnuplot installed in a non-standard location, see the 'gnuplot_binary' function


I've done an apt-get remove -purge gnuplot octave followed
by a subsequent install and still get the same message.  Any thoughts?  I'm using Jaunty.


For some reason the reinstall with octave was not installing gnuplot

I tried apt-get install gnuplot and it went through and THOUGHT it was there, but when I did a which gnuplot it didn't show up.

I then went through and apt-cache search | grep gnuplot

and systematically install gnuplot-X11 and python-gnuplot.

I then did a aptitude reinstall gnuplot and things work ...
Weird.

---

### Post by IAmCorbin on 2012-03-05
```
sudo aptitude reinstall gnuplot
```
also just worked for me while trying to compile octave 3.6.0 on Ubuntu 10.04. It is building now. Strange, as I had just installed it for the first time prior to this.

Thanks!

---

