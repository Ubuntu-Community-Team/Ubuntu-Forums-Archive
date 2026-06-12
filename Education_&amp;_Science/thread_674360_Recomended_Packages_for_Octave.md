---
title: "Recomended Packages for Octave?"
date: 2008-01-21
forum: Education &amp; Science
---

### Post by fulgencio on 2008-01-21
Hi,
Would some experienced Octave user please tell me the packages I should install to have a working installation. I would like to stick to the synaptics specification (not interested in a super recent version of Octave). I'm specifically interested in the Octave-forge package (more specifically the plot3 function), because even though Octave is working in my computer it seems the package Octave2.9-forge is not doing what it should.
Thanks in advance

---

### Post by thisismalhotra on 2008-01-22
You probabaly need octave 3.0 and I recommend that .. it is much much better than octave 3.X, 
Also, did you install both octave and octave-forge 2.9 if yes it should work fine ... if no try installing both. If still nto working uninstall and install again. ...

Also, let me know what functions you use and I can maybe help??

---

### Post by zeus77 on 2008-01-22
For Gutsy, my recommended install would be:

# base octave 2.9 w/gnuplot, and speed boost w/Pentium 4+
sudo apt-get install atlas3-sse2 octave gnuplot

# adds more functions, better matlab compatibility
sudo apt-get install octave2.9-forge

# full documentation
sudo apt-get install octave2.9-info octave2.9-doc octave2.9-htmldoc
gnuplot-doc


The 'plot3' command works just fine, but for some reason 'surf' seems to be undefined.

zeus77

---

### Post by thisismalhotra on 2008-01-22
For me surf works just fine in Octave 3.0 and I have been using that for a while. IF you guys need a .deb for that send me an PM with your email and I will send it ..

---

### Post by fulgencio on 2008-01-22
I reinstalled octave2.9 and octave2.9-forge using synaptics and all the documentations packages currently I have installed:

-Octave
-Octave2.9
-Octave2.9-doc
-Octave2.9-forge
-Octave2.9-headers
-Octave2.9-htmldoc
-Octave2.9-info

 everything works fine now. probably will look for something to improve graphics though.
thanks.

---

### Post by fulgencio on 2008-01-22
I have  no surf either. mesh works perfect though

---

### Post by thisismalhotra on 2008-01-23
> **fulgencio said:**
> I have  no surf either. mesh works perfect though
Hey fulgenico,

Send me your e-mail ID in private message I will send you a .deb file for newest version of octave which is 3.0. surf is defined in that and other things too which comes real handy..

see this:

[http://www.gnu.org/software/octave/NEWS-3.html](http://www.gnu.org/software/octave/NEWS-3.html)

---

### Post by zeus77 on 2008-05-02
Incidentally, for Hardy Heron, my recommended list of packages would be:

# octave, gnuplot, with Pentium 4+ speedup
sudo apt-get install libatlas3gf-sse2 octave gnuplot

# documentation
sudo apt-get install octave3.0-doc octave3.0-htmldoc octave3.0-info gnuplot-doc


Note that the sse2 (i.e. Pentium 4+ extensions) library name has changed slightly for hardy+octave3.  If you have an older Pentium or AMD processor, you should replace libatlas3gf-sse2 with one of: libatlas3gf-{3dnow, base, sse}, depending on your situation.

If you don't explicitly include a libatlas library when installing octave, then libblas3gf and liblapack3gf will be installed (as they are dependencies), leading to slower performance.  

Also, note that the 'surf' routine now works fine, as it is included in octave 3.0 (but was not included in octave 2.9 which was packaged with Feisty Fawn).  Finally note that the 'forge' routines seem to be missing from the repositories... this is unfortunate.


zeus77

---

### Post by zeus77 on 2008-11-16
installing all the necessary packages in intrepid (8.10) is as easy as simply installing the 'octave' package:
```
# octave (includes gnuplot as dependency)
sudo apt-get install octave

# documentation (optional)
sudo apt-get install octave3.0-doc octave3.0-htmldoc octave3.0-info gnuplot-doc

```
if you're running the 32-bit x86 version of intrepid, you may want to install the atlas sse2 library.  also, good news: they put the octave forge routines in synaptic this time around.  there's not one single package, but a bunch of them (e.g. octave-signal, octave-statistics, etc).

---

### Post by levelup2 on 2008-12-01
is really useful for me, I am glad to read it here.

---

