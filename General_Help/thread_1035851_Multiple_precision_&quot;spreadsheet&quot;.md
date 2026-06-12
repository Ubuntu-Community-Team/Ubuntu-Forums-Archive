---
title: "Multiple precision &quot;spreadsheet&quot;"
date: 2009-01-10
forum: General Help
---

### Post by Taxman415a on 2009-01-10
Does anyone know of any applications like that for Ubuntu? 

I'm looking to play around with some mathematical series and I'd like to explore their convergence. OpenOffice.org cuts off at 20 or so decimal digits which is far too few. I know I can use tools like dc to get as much precision as I like, but I want to find something easy along the lines of a spreadsheet, so I can track each of the numbers in the formulas I'm using.
Ideally I could use it in a classroom.

I tried searching but I couldn't confirm that GNU Octave could do multiple or infinite precision. I don't know about any of the other CAS systems, but many of those certainly aren't easy to use.

---

### Post by aheckler on 2009-01-10
Have you tried Gnumeric? It's in the repos.

---

### Post by Taxman415a on 2009-01-10
> **aheckler said:**
> Have you tried Gnumeric? It's in the repos.

Good thought, but according to [http://www.gnu.org/software/gnumeric/gnumeric.html](http://www.gnu.org/software/gnumeric/gnumeric.html) it's listed as a future project. I did try installing it and it does display 30 vs 20 floating point digits for OO.org but seems to carry about the same number of digits internally.

---

### Post by jpkotta on 2009-01-10
**wxmaxima:**
```
fpprec:1000
bfloat(%pi)
```

**octave:**
You need the symbolic package.  The one in Intrepid is apparently broken, so you'll need the octave-headers package, the symbolic tarball from [http://octave.sourceforge.net/symbolic/index.html](http://octave.sourceforge.net/symbolic/index.html), and build it with (from octave)
```
pkg install /path/to/tarball/symbolic-1.0.7.tar.gz
```
Then it should crunch for a while and when it's done, 
```
pkg list
```
should show it.  Then,
```
digits(1000)
Pi
```

**wcalc:**
```
\p 1000
pi
```

---

### Post by jpkotta on 2009-01-10
Also, all of the programs I listed aren't nearly as good as Mathematica, but that's expensive.

---

### Post by Taxman415a on 2009-01-11
Thank you very much. I guess that does answer that there isn't anything really easy to do what I'm looking for, but wxmaxima might do the trick. I couldn't find anything in the documentation on why it truncates my output as in the following though.

(%i1) fpprec:100;
(%o1) 100
(%i2) bfloat(%pi);
(%o2) 3.1415926535897932384626433832[43 digits]6286208998628034825342117068b0

I don't think I'll have too much trouble figuring out how to put each part of the sum calculation in it's own array so I get a0, a1, a2, ... in one array and b0, b1, b2, ... in another, etc, and the final sum in another. I recall doing it in Maple or Mathematica in the past. The wxmaxima documentation seems a little confusing on it, but I think I can get it.

I still may end up using dc and registers and their stacks since I'm dealing with integers and floats and nothing more than square roots.
Thanks for the tips.

---

### Post by Taxman415a on 2009-01-12
> **jpkotta said:**
> 
**octave:**
You need the symbolic package.  The one in Intrepid is apparently broken, so you'll need the octave-headers package, the symbolic tarball from [http://octave.sourceforge.net/symbolic/index.html](http://octave.sourceforge.net/symbolic/index.html), and build it with (from octave)
```
pkg install /path/to/tarball/symbolic-1.0.7.tar.gz
```

Just for future browsers of this forum, the symbolic package also requires GINAC, which means you need the libginac-dev package if you want to build the symbolic package from source. Hopefully the bug in the pre-packaged one gets worked out though.

---

