---
title: "scipy"
date: 2007-02-26
forum: Education &amp; Science
---

### Post by jeremytaylor on 2007-02-26
Hi there, 
does anyone use f2py with scipy? I'm having some problems getting it to work. In particular I get error messages along the lines of

error: file '/usr/lib/python2.4/site-packages/numpy/f2py/src/fortranobject.c' does not exist

I have scipy installed (or it wouldn't have even got this far) but was wondering if i also need scipy-core installed. If this is the case then there seems to be a problem, trying to install it forces the removal of scipy. It claims that scipy depends on scipy-core but currently these packages won't allow themselves to be installed at the same time.

Any help would be much appreciated.

Jeremy

---

### Post by tweedledee on 2007-02-26
> **jeremytaylor said:**
> Hi there, 
does anyone use f2py with scipy? I'm having some problems getting it to work. In particular I get error messages along the lines of

error: file '/usr/lib/python2.4/site-packages/numpy/f2py/src/fortranobject.c' does not exist

I have scipy installed (or it wouldn't have even got this far) but was wondering if i also need scipy-core installed. If this is the case then there seems to be a problem, trying to install it forces the removal of scipy. It claims that scipy depends on scipy-core but currently these packages won't allow themselves to be installed at the same time.

Any help would be much appreciated.

Jeremy

Scipy-core is an old name for Numpy (which in turn comes from the old Numeric).  Scipy-core is old and not particularly useful.  You should instead try installing the numpy package (assuming scipy didn't install it already) and/or the numpy-dev package (which probably has the source code f2py is looking for).

---

### Post by jeremytaylor on 2007-02-27
Great, thanks that worked! 
Jeremy

---

