---
title: "Calling scilab/octave from terminal"
date: 2008-11-08
forum: Education &amp; Science
---

### Post by fredscripts on 2008-11-08
Hi!!

I'm just curious about how could I call scilab or octave within the terminal. 

The target is to call functions such as for solving linear system of equations from a perl/python/ruby script and work with scilab/octave output.

So say for example in a script
```

...
solution = system( octave/scilab [params]);
...
```

So for example. How one could do that simple task:

- Ask the user to enter a matrix and a vector (modeling a system of linear equations) either pointing to a file or in standard input.

- Within the script, call scilab/octave to solve the system with correct parameters of scilab/octave functions.

- Catch the result within the script and show it to the user.


Thanks!

---

### Post by WW on 2008-11-08
If you are using python, why bother with scilab or octave?  Use [scipy](http://www.scipy.org/), [numpy](http://numpy.scipy.org/) and [matplotlib](http://matplotlib.sourceforge.net/).

---

### Post by fredscripts on 2008-11-09
Thanks for answering.

Yes sure I could use language libraries to do some task. But I imagine that those libraries doesn't has all the functionality that has matlab/octave/scilab, so it'd be interesting giving those programs the "hard work" within a script and then keep going.

---

