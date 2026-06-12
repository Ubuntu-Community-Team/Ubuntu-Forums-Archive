---
title: "Best open source competitor to Matlab?"
date: 2010-08-30
forum: Education &amp; Science
---

### Post by Zorgoth on 2010-08-30
I know about octave, which seems to be pretty good, but there are a number of other programs and I am wondering if octave is best or not.  I know that octave is designed to be compatible with Matlab (which will make things easier for me since I just spent three months working in Matlab for a summer job), but I don't know if it is the best overall system or not.

Is octave designed to be a complete copycat of Matlab or does it have its own functions/optimizations?  It seems like if it is just a copy that would ultimately force it to be permanently inferior to Matlab, in much the same way that OpenOffice will never handle .docs as well as MS Word (while it would obviously have the advantage that octave code could be run in Matlab, but I don't care about that for my purposes).

I probably will use C++ for any really intensive work (although I may implement it in an interpreted high-level language first), but performance is definitely an important factor, as are debugging/plotting capabilities, and the features of the shell itself (e.g. matlab has a very nice shell, for example if you type in the first part of a command and use up, you cycle through only commands starting with that segment).  Emacs integration is another big feature since I do basically all of this kind of work in emacs (even when using Matlab).

I am perfectly willing to learn a new system if I think it is better, so the fact that octave is a lot like Matlab isn't that big of a deal.

So out of all the open source alternatives then, is octave the best with regard to performance/debugging/shell features or are there better choices if I do not require Matlab compatibility?

---

### Post by FreeTheBee on 2010-08-30
I cannot say if it is better or worse, but another option would be python with numpy, scipy and matplotlib.

---

### Post by apmcd47 on 2010-08-30
You could look at [GDL]("http://gnudatalanguage.sourceforge.net/") which is an open source reimplementation of [IDL]("http://www.ittvis.com/ProductServices/IDL.aspx?gclid=CKDKkIn44aMCFQX92AodayFrAA"). It's not quite there yet, according to the home page, but it might be worth a look.

IDL is a Fortran-like programming languge for data manipulation and visualisation and is used a lot in Space and Medical research. I don't really know Matlab very well, so this could be a poor suggestion.

Andrew

---

### Post by avnibu on 2010-08-30
Hello,

A first timer here.

I am not an expert on this subject but I want to follow a similar path as yours and learn an open source alternative to Matlab. When researching, I found [this]("http://en.wikipedia.org/wiki/Comparison_of_numerical_analysis_software") on wikipedia and from what I heard [Scilab]("http://en.wikipedia.org/wiki/Scilab") is a worth to mention runner up for an o.s. matlab substitute.

Cordially,
Avni

---

### Post by kaspar_silas on 2010-08-31
You don't mention what field you work in. It's a nice idea to quickly scan the job market for your field and see what people want. It's not cool being a fortran legend if everyone in your next workplace uses Java. 

O octave is very close to a copycat of Matlab. Mostly scripts will run in both just as close.

I'd guess python sounds ideal for you. Firstly it's growing in popularity, sort of "sensible" for debugging, has vi integration with autocomplete as you desribe (not sure about emacs), is normally pretty damn fast and as mentioned above is very extendable with the thousands of great libraries around. Plus if you are any good at C/C++ it's easy to incorporate this into python code.

---

### Post by Simian Man on 2010-08-31
> **Zorgoth said:**
> Is octave designed to be a complete copycat of Matlab or does it have its own functions/optimizations?  It seems like if it is just a copy that would ultimately force it to be permanently inferior to Matlab, in much the same way that OpenOffice will never handle .docs as well as MS Word (while it would obviously have the advantage that octave code could be run in Matlab, but I don't care about that for my purposes).

That is the problem with a lot of open source software.  They spend a lot of time chasing moving targets (with less resources) and never get to the point where they can try doing anything new.

Mathematica can run natively on Linux, but it isn't open-source and it isn't free.  It's more powerful than Matlab though not quite as fast.

---

### Post by kaspar_silas on 2010-08-31
I love Mathematica, it is the last proprietary software I use. Perfect for when you need to quickly test out an idea. There is a blinding number of v.fast mathematical functions and masses of random scientific data (look it up, it's crazy). It also has probably the only built in help I know that you can happily waste hours in. 

However the mathematical focus is also somewhat fundamental to the software and if you are not very mathematically minded really this is not the software for you. You'll spend as much time on google decoding what the new error messages means. It's also a nightmare to port code after as you always use the powerful built-in functions.

It's also worth pointing out that not free is almost an understatement. A non student license is over £2000.

---

### Post by Zorgoth on 2010-08-31
I definitely think that the Python route looks most attractive.  

Matlab also runs natively on Linux - I just don't want to get hooked on a product that might end up costing me thousands of dollars after I am out of school - there the same problem clearly exists with Mathematica.

I am studying mathematics and although I previously was planning to study pure mathematics I think I am leaning more toward applied work after my internship.

SciPy/NumPy does use ATLAS, although you have to specifically install ATLAS rather than the default library (which is slower).  I've done some playing around and I quite like the syntax of SciPy (using it in ipython).  I haven't tried debugging yet, but I am sure that that will work fine since Python is a major programming language.

---

### Post by ahmatti on 2010-09-01
I have moved from Matlab to using [R]("http://www.r-project.org") or [SciPy]("http://www.scipy.org"). It really depends on what kind of work you do. If you work a lot with arrays, signals, linear algebra etc. then I think python+scipy+matplotlib is a bit better and the performance is in loops etc. is better than for R. On the other hand R offers more extension packages and is IMO more complete in terms of functionality. 

I use R a lot for Machine Learning, but I rather use SciPy for signal processing problems. Both are easy to extend with C++ and I feel they are both generally better than Matlab. See [Rcpp]("http://dirk.eddelbuettel.com/code/rcpp.html") and [Scipy.weave]("http://www.scipy.org/PerformancePython"). Both also have good Emacs integration, [ESS]("http://ess.r-project.org/") is actually the best Emacs mode I've used.

---

### Post by surfer on 2010-09-01
i like [sage]("http://www.sagemath.org/"). extensive, under active development and with a python interface.

---

### Post by kleskjr on 2010-09-01
one more for python.
1.5 years ago I moved from matlab to python and definitely I think python+numpy is better, more flexible. There are also tons of different open-source libraries (for image processing, ANN, etc.)

---

### Post by mechsin on 2010-09-01
I agree with those siting Python as a good alternative. I am an engineer and do lots of data analysis and program heavily in Matlab. Do to some limitations with gui development as well as lack of hdf5 file support I have been migrating to python. I also create data analysis tools for people to use that don't know how to program Python makes this easier. Python also has lots of good libraries that can be downloaded that make it very comparable to Matlab if not superior because Python is more of a full blow programming language that just does somethings that Matlab will never support. I currently use the scipy/ipyton/numpy packages with matlibplot. I'm not super happy with the plotting vs Matlab but its ok. If you go here they list most of the major packages available.

[HTML]http://wiki.python.org/moin/NumericAndScientific[/HTML]

---

### Post by ssam on 2010-09-02
+1 for python/numpy/scipy/matplotlib. the numerical tools are good, and you have the whole python libraries to hook in. have a look at f2py if you want to hook in bits of C.

if you are coming from matlab to python have a look at
[http://www.scipy.org/NumPy_for_Matlab_Users](http://www.scipy.org/NumPy_for_Matlab_Users)
there are a few subtle differences worth knowing about.

---

### Post by manzdagratiano on 2010-09-03
Octave for most purposes, SAGE for all others (specifically for replacing Mathematica)

---

### Post by kaspar_silas on 2010-09-06
> **PeterRossy said:**
> Mathematica's source is easy to get opened but it's really very-very powerful instrument.

Eh, how exactly does one do that? Are you saying it's easy to crack open the source? That does not seem a valid solution to obtain workplace software. Or maybe I misunderstood you. 


Also yes Sage is great and it's a great project but it is nowhere near as polished or generic a product as Mathematica. I hope sage gets there but just compare the overview of the products to see the difference.

SAGE:
[http://www.sagemath.org/tour.html]("http://www.sagemath.org/tour.html")
MATHEMATICA:
[http://www.wolfram.com/products/mathematica/quickoverview/#]("http://www.wolfram.com/products/mathematica/quickoverview/#")

---

### Post by Axolotl9250 on 2010-09-06
> **ahmatti said:**
> I have moved from Matlab to using [R]("http://www.r-project.org") or [SciPy]("http://www.scipy.org"). It really depends on what kind of work you do. If you work a lot with arrays, signals, linear algebra etc. then I think python+scipy+matplotlib is a bit better and the performance is in loops etc. is better than for R. On the other hand R offers more extension packages and is IMO more complete in terms of functionality. 

I use R a lot for Machine Learning, but I rather use SciPy for signal processing problems. Both are easy to extend with C++ and I feel they are both generally better than Matlab. See [Rcpp]("http://dirk.eddelbuettel.com/code/rcpp.html") and [Scipy.weave]("http://www.scipy.org/PerformancePython"). Both also have good Emacs integration, [ESS]("http://ess.r-project.org/") is actually the best Emacs mode I've used.

I agree I think R is probably the most versatile you could use, there are also a LOT of mailing lists and forums for it and is renowned for it's modelling and award winning publication quality graphics. Rkward is also a brilliant tool for it and Sweave and odfWeave are definite boons when writing up your work.

---

