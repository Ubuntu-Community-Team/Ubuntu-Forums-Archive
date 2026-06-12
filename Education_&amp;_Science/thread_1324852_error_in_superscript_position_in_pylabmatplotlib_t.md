---
title: "error in superscript position in pylab/matplotlib text"
date: 2009-11-12
forum: Education &amp; Science
---

### Post by adasilva on 2009-11-12
Hello all, I can't be the first one to encounter this problem, but I couldn't find anything in a google search.

I am using matplotlib to generate some plots for a paper. I need to use a small font (6pt) in all text on the plot, but I run into a problem when using superscripts, for example, an x-axis label: 
```
pylab.xlabel('cm$^{2}$',fontsize=6)
```
gives me this:
[IMG]http://www.phys.psu.edu/~adasilva/image.png[/IMG]

More details:
matplotlib.__version__ = '0.91.2'
numpy.__version__ = '1.3.0'

numpy was installed from the latest svn using:
```

sudo python setup.py build
sudo python setup.py install

```

I've been messing around with the matplotlibrc file, which is why my axes are bold. 

When I set the option text.usetex=True in the matplotlibrc file, I get a mess of errors, so that is not an option at this time.

I am using ubuntu 8.04

Any ideas?

---

### Post by ahmatti on 2009-11-18
I had the same behavior with matplotlib 0.91.2, but was able to fix it by upgrading to the newest version 0.99.1. It is easy to install from source.

---

### Post by adasilva on 2009-12-12
I just upgraded numpy, scipy, and matplotlib, and it works beautifully now. Thanks for the advice.

---

