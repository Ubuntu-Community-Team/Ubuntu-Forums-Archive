---
title: "Scilab or Octave"
date: 2007-10-28
forum: Education &amp; Science
---

### Post by bioxg on 2007-10-28
Hi, I'm a new user  in Linux, but i very like Linux, of course Ubuntu.
i want use my xubuntu (ppc) to learn matlab, i have two choice: one is Octave, the other is Scilab.
which is better? thank you!

---

### Post by ac1201 on 2007-11-05
Octave.

Actually I've never used Scilab, so maybe it's awesome.

I use Octave - the most recent version has taken *huge* strides forward in terms of similarity to Matlab, and functionality.

You'll find graphics are still a little different, and will probably want to use Gnuplot or a similar tool for finished-quality graphics.

---

### Post by thisismalhotra on 2008-01-08
Hey bioxg,

I am a new user too but I used both scilab and octave. If you are accustomed to matlab and don't want to learn anything new and just start programming right away definitely octave is the way to go.

If you plan to use octave use OCTAVE 3.0, which is way up there as compared to 2.9 or 2.1 (which you get from synaptic). So you might have to download an build it from source. Please note it does not have a GUI and is a shell based application.

Also, Scilab is pretty similar but not the same, I use both and I find them to be equally comparable. Scilab comes with an IDE and an editor to code so is more integrated but you will have some learning curve.

So take you pick
Happy number crunching

---

### Post by Ionosphere on 2008-03-22
I actually prefer Scilab. I've been using Octave for a while but the gap between Octave and Matlab is bigger that the one between Scilab and Matlab so my prof would never be able to run Octave files that I sent him without making some adjustments to them. I also find Scilab a bit cleaner and more functional. But maybe it's just me.

---

### Post by PeterP24 on 2008-03-23
I'm a Scilab user: my opinion is that this program is very close to Matlab. There are minor diferences in the name of some functions, and some basic comands, and of course scilab doesn't have all the functions from Matlab but I believe that after you  learn Scilab you can easily adapt to Matlab. From my experience : after writing  a long script in Matlab I've discover that the company to whom the script was adressed didn't had Matlab. They suggested me 2 alternatives : Excel or Scilab. So  what I did was to run the Matlab script in Scilab (with the .sci extension added). For my surprise, only 3 minor error apeared :> 
- first, the comentaries in scilab begin with // while in Matlab are with %
- second, at the beginnig of the script a data file data.m was loaded with the comand "run data.m" in Matlab. In Scilab it became exec('data.sci')
- third, some built in constants like PI in matlab are used like %PI in Scilab.
There are of course other diferences, like the fact that if you write your own functions in Scilab you have to load them with the comand getf("") while in Matlab you don't need to load the functions scripts (they must be in the matlab search path of course or the curent directory).

If you want something similar to Simulink you could use Scilab alternative - Scicos. Most of my coleagues consider Scilab as a open source alternative to Matlab (not the only one of course). 
Finally, I recommend you to visit the home site of Scilab to view  the available extra documentation. 

Peter

---

### Post by raja on 2008-03-24
While scilab and Octave are the commonly considered alternatives, you may also want to consider the combination of Python + Scipy + Matplotlib. Can have all the functionality with more flexibility at the expense of a little bigger learning curve. Especially worth considering if you are already familiar with Python.

---

### Post by sylvestre on 2009-01-06
Until it is not officially included in Debian/Ubuntu, an Ubuntu repository for the version 5 is available: 
[http://www.scilab.org/team/sylvestre.ledru/](http://www.scilab.org/team/sylvestre.ledru/)

---

### Post by in_flu_ence on 2009-01-06
I personally prefer octave over scilab. I normally have alot of matlab files from previous workers and converting them into scilab using the built-in convertor normally will cause minor errors. Whereas I can just run the .m files as it is in octave. Far more convenient for me in the sense and octave tends to work perfectly fine in all the previous matlab codes written. It maybe just me for using only a limited set of functions.

I manage to do loops, sort data and plot the sorted data in gnuplot + saving the files in csv.

---

### Post by cdnaerogeek on 2009-01-09
I second raja's comment. Python + Scipy + Matplotlib will do most, if not all, of what you want to do in Matlab. It is also much more extensible - being part of Python already - and personally, I prefer the nice object-oriented setup of matplotlib.

Even if you don't know any Python to start with, it's quite easy to learn on your own.

---

### Post by nico80 on 2009-07-07
I would also like to remind you of another really powerful alternative to all the nice software you mentioned, that is, of course, R!

---

### Post by perroazul on 2009-07-08
> **in_flu_ence said:**
> I personally prefer octave over scilab. I normally have alot of matlab files from previous workers and converting them into scilab using the built-in convertor normally will cause minor errors. Whereas I can just run the .m files as it is in octave.

I agree with in_flu_ence. I have done several tests of octave+gnuplot with what I consider to be fairly complicated matlab scripts, and they execute without any problems (and I didn't have to make any changes to them).

---

### Post by ahmatti on 2009-07-21
I think the choise really depends on why you want to learn Matlab... If you know that you need to use matlab in your studies/job and want something that comes as close as possible then use Octave.

On the other hand if you just want to learn a good  language for scientific computing choose R or Python. There is an R vs Python thread running that might help you choose.

In any case I suggest that you forget Scilab.

---

### Post by in_flu_ence on 2009-07-23
I have actually find Python to be very interesting and promising. Not difficult to learn but probably not for task that needs the speed like C++ and Fortran.

Advice?

---

### Post by ahmatti on 2009-07-24
You can make Python code run faster with Psyco (kind of JIT) or use Cython [www.cython.org](www.cython.org) to write C-extensions for Python to speed up the most time consuming parts of your project. For my projects interpreted languages are fast enough so I haven't actually needed to use Cython, but I've read some examples that seem simple enough. Python also has interfaces for some C-libraries that do the heavy processing for you like opencv for machine vision and libsvm for support vector machines.

---

### Post by Zorgoth on 2010-08-30
The python option sounds interesting, but I do have some questions.

How hard is it to interactively code in Python?  The main advantage of Matlab is that you can run your programs interactively, easily get the output of a function (like the dimensions of an array or the value of a number) just by typing it (for example if foo=5, in matlab you can just type foo and it will output foo = 5 - is there comparable functionality in SciPy or would I have to type something like 'print foo?')

Also, how is the performance of the fundamental functions?  My guess would be that for looping and such Python code would be faster than Matlab, but when performing an individual operation like a massive matrix multiplication Matlab uses C/ATLAS.  For operations like that will SciPy be able to offer any kind of comparable speed?

Reading up on it it does look like NumPy does use some compiled C functions.  Do these functions use ATLAS?  Also, do the SciPy extensions ever use compiled C/Fortran or are they all python+numpy?

---

### Post by xadder on 2010-09-02
Considering interactivity, if you go the python+numpy+matplotlib (pylab) route then ipython is your friend. You can edit scripts from within ipython, and the script will be run immediately on closing. This gives a fast write-plot cycle that encourages good scripting. You can also run ipython -pylab to get some features loaded automatically, but it is probably better to make your script import those features.

---

### Post by manzdagratiano on 2010-09-03
> **Ionosphere said:**
> I've been using Octave for a while but the gap between Octave and Matlab is bigger that the one between Scilab and Matlab so my prof would never be able to run Octave files that I sent him without making some adjustments to them.

I don't agree with this statement. Octave code is identical to Matlab code; most importantly, and program written in Matlab should work in Octave, with the very minuscule exceptions given on the octave website, though octave supports broader features than Matlab, like the ++ operator.

I  use Octave for all of my coding, and I run these programs routinely on a Matlab server. If you want compatibility, just write your code as if in Matlab and Octave WILL run them.

---

### Post by FreeTheBee on 2010-09-03
> **in_flu_ence said:**
> I have actually find Python to be very interesting and promising. Not difficult to learn but probably not for task that needs the speed like C++ and Fortran.

Advice?

You can mix in fortran using f2py.
[http://www.scipy.org/F2py](http://www.scipy.org/F2py)

---

### Post by radioboy on 2010-09-17
Also consider Sage as an alternative: [http://www.sagemath.org/](http://www.sagemath.org/)
You can store notebooks of your calculations.

I really don't use Sage for now, but the combination Python+Numpy+Scilab+Matplotlib+iPython and some Sympy. 
Besides iPython for interactivity you can test: Dreampie and BPython.
[http://dreampie.sourceforge.net](http://dreampie.sourceforge.net)
[http://bpython-interpreter.org/](http://bpython-interpreter.org/)

When I need to write longer programs that will surely need more debugging, I use the IDEs Spyder and Eric.
[http://code.google.com/p/spyderlib/](http://code.google.com/p/spyderlib/)
[http://eric-ide.python-projects.org](http://eric-ide.python-projects.org)

Spyder currently supports the internal use of ipython as a console mode.
The good thing about these IDEs is that you can examine the contents of arrays and other stuff more easily. Spyder also allows you to store the objects in memory for the next session.

---

### Post by AFarris01 on 2010-10-26
I know this thread started a good while ago, but I'll throw my input in anyway...

I recently discovered Sage and Scilab and started using both alongside Matlab for doing calculations/plots/etc for papers and other assorted silliness, and they each have their ups and downs. I'll cover them each briefly:

**Octave- **
Octave has been really great to me, and I've used it extensively for a number of years. I began using Octave an umber of years ago because I needed to use Matlab to work on a project from home, but I didn't have the resources to acquire a copy. It was then I discovered Octave, and used it to great success in my project. Over the years I've written many scripts in Octave, and I've only ever run into a few issues converting them to Matlab... namely I've come to rely on some key features in Octave that aren't present in Matlab (like the print to eps+LaTeX feature). I also ran into a problem that Octave did not solve accurately (root-loci problem using the controls package, but thtas another story), but all in all I've found it to be a very effective replacement for Matlab.

**Scilab- **
I have not used Scilab as much as Octave or Sage, but I have found it to be very capable at performing calculations. I haven't had much experience setting it up to export data for papers, but for quick dirty calculations it's at the very least equivalent compared to octave. The only thing I've noticed in general is Scilab (in script mode) seems to start up/run faster than Octave does, but I don't have any concrete proof of this yet (I do intend to do a study on it though, if the 'time' program in the Ubuntu repos will ever get fixed...).

**Sage- **
Sage is still the new kid on the block in my arsenal of tools, but so far, it has proved itself to be a fantastic tool.  One of my preferred uses for it so far is its flexible symbolic math capabilities. I have made extensive use of this over the last several weeks, and it has proven itself far superior to most other tools at this task. I also greatly appreciate the fact that it includes a system for doing unit comparison/conversions within the program, which works very well. The interface for that particular tool could be a little better (it's a little cumbersome to use the default notations, i.e. for meters/second it would be units.length.meter/units.time.second) but it's easy to work around.  My favorite feature of Sage though, is the LaTeX integration... if you write reports/papers with LaTeX, then this feature is to-die-for. Basically, it allows you to import an extra package at the start of your document(sagetex), and perform Sage calculations/operations (including plotting) directly inside the LaTeX document! you can literally use it to perform symbolic or numerical calculations for you with the power of Sage, then automatically dump them into LaTeX for your report(symbolically or numerically). I've even used this feature for writing out a document on how to do a particularly lengthy derivation, and I was able to do it with Sage+LaTeX by doing little more than defining the initial equations, and the important operations (equation.derivative(), M.substitute(h=some_other_formula) etc... ). 

That's all I've got for now... hopefully this information will prove useful to somebody in the future, and all this typing will not have been in vain :)

---

