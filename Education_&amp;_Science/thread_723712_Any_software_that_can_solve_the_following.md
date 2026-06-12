---
title: "Any software that can solve the following?"
date: 2008-03-13
forum: Education &amp; Science
---

### Post by in_flu_ence on 2008-03-13
I am trying to convert a few equations into power series like what's shown in 

[http://reference.wolfram.com/mathematica/ref/SeriesData.html](http://reference.wolfram.com/mathematica/ref/SeriesData.html)

Can this be achieved in octave or any other software? Preferably used in ubuntu.

Is there anywhere I can read on how to do it manually? I seem to have forgotten a big chunk of Maths..


Thanks.

---

### Post by WW on 2008-03-14
> **in_flu_ence said:**
> I am trying to convert a few equations into power series like what's shown in 

[http://reference.wolfram.com/mathematica/ref/SeriesData.html](http://reference.wolfram.com/mathematica/ref/SeriesData.html)

Can this be achieved in octave or any other software? Preferably used in ubuntu.

There are several tools that you could use.  For example, in maxima (or xmaxima):
```

(%i1) taylor(exp(x),x,0,5);
                               2    3    4    5
                              x    x    x    x
(%o1)/T/              1 + x + -- + -- + -- + --- + . . .
                              2    6    24   120
(%i2) taylor(exp(x),x,1,5);
                                     2             3             4
                           %e (x - 1)    %e (x - 1)    %e (x - 1)
(%o2)/T/ %e + %e (x - 1) + ----------- + ----------- + -----------
                                2             6            24
                                                                      5
                                                            %e (x - 1)
                                                          + ----------- + . . .
                                                                120
(%i3) 



```
Other symbolic algebra programs include Yacas and Axiom; there are a few others, too.

If you know a little C++, you can do this with the GiNaC library:

**gseries.cpp**
```

#include <iostream>
#include <ginac/ginac.h>

using namespace std;
using namespace GiNaC;

int main(int argc, char *argv[])
{
symbol x("x");
ex f = exp(x);
cout << "Taylor series about x=0:   " << f.series(x==0,5) << endl;
cout << "Taylor series about x=1:   " << f.series(x==1,5) << endl;

return(0);
}

```
Compile and run:
```

$ g++ gseries.cpp `pkg-config --cflags --libs ginac` -o gseries
$ ./gseries 
Taylor series about x=0:   1+1*x+1/2*x^2+1/6*x^3+1/24*x^4+Order(x^5)
Taylor series about x=1:   (exp(1))+(exp(1))*(-1+x)+(1/2*exp(1))*(-1+x)^2+(1/6*exp(1))*(-1+x)^3+(1/24*exp(1))*(-1+x)^4+Order((-1+x)^5)
$ 

```


> **in_flu_ence said:**
> 
Is there anywhere I can read on how to do it manually? I seem to have forgotten a big chunk of Maths..

Take a look [here](http://en.wikipedia.org/wiki/Taylor_series).

---

### Post by in_flu_ence on 2008-03-14
Thanks. Life just gets better with Linux.

---

### Post by ljd65536 on 2008-03-16
I installed maxima with the Synaptic package manager. But I had to add this link for help to work.

sudo ln -s /usr/share/maxima/5.12.0/doc/info/maxima-index.lisp.gz maxima-index.lisp.gz

---

### Post by in_flu_ence on 2008-03-16
I actually refer to the website for help or google for solution. Think it is quicker and more specific to problem.

Anyway, WW's post has helped me alot in what i want from maxima.

But nice info for those who are using maxima as well

---

