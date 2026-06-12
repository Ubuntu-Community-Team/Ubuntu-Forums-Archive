---
title: "No mathcad for Linux. So what should I try?"
date: 2009-05-23
forum: General Help
---

### Post by Liolikas on 2009-05-23
There is already same old tread , but with not working links etc.
So time to ask one more time.

---

### Post by cmost on 2009-05-23
Try Octave (especially QtOctave, which is very simliar to Mathcad.)  You can find more information here:

Octave
[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)

QtOctave
[http://qtoctave.wordpress.com/what-is-qtoctave/](http://qtoctave.wordpress.com/what-is-qtoctave/)

Octave-GTK (a GTK+ binding for Octave)
[http://octave-gtk.sourceforge.net/](http://octave-gtk.sourceforge.net/)

Good luck!

---

### Post by Liolikas on 2009-05-23
Thx, but:
> 
QtOctave, which is very simliar to Mathcad.

Sry no:
> 
It provides a convenient command line interface for solving linear and nonlinear problems numerically, and for performing other numerical experiments using a language that is mostly compatible with Matlab. 

It is like Matlab and I want simmilar to Mat**cad**, but still that Octave very good, but not exactly what I want.

Any other suggestions?

---

### Post by cmost on 2009-05-23
Oops!  Sorry, my mistake.  How about Maxima?  It seems as though it might work similarly to Mathcad.  Here's some information.

Maxima
[http://maxima.sourceforge.net/](http://maxima.sourceforge.net/)

You could also try to install Mathcad in Linux directly using WINE (some have reported success.)

Information on installing Mathcad in WINE
[http://dopelover.110mb.com/pub/mcd-tutorial/](http://dopelover.110mb.com/pub/mcd-tutorial/)

As a side interest, here is a good article on the state of scientific software for Linux.  As a chemist, I often find myself in the same situation as you; searching for a good FOSS tool to replace a proprietary one that some University shoves down your throat.  :-)

[http://www.linux.com/archive/articles/56966](http://www.linux.com/archive/articles/56966)

Best of luck!

---

### Post by Liolikas on 2009-07-26
I got info that Mathcad 5 works fine on wine and I am using it now.
Quite old but hey it works. :)

---

### Post by Peter K Nicol on 2009-12-15
I recommend that you try wxMaxima. It works well in Ubuntu or Windows
There are advantages and disadvantages. Mathcad offers a wonderful environment for engineering calculations that really can't be beaten but it is expensive and only works in Windows. wxMaxima has a good front end and is excellent mathematically. It doesn't handle units well and the graph output could be slicker but it carries out all sorts of maths. I use it with students up to 2nd year university level (HND) for matrices and calculus up to solving ODEs and Fourier transforms. The program is being constantly updated - the front end is really good now and most of the common functions are on a right click menu. I can offer some help with the basic aspects of this if you are interested. Also try Geogebra - another open source program that is constantly improving - excellent graphs!

p.s. don't load the 5.20 version yet as there are a few bugs to be ironed out yet (wxMaxima 8.4 + Maxima 5.19 mostly works well)

---

### Post by keplerspeed on 2009-12-15
It goes a bit like this:

For matrix mathematics (ie every item is treated as a matrix) based software like MATLAB, you have a few open source (linux) alternatives:

1) Octave + the Qt Octave front end. Works just like MATLAB, looks very much the same and will be compatible with 90% of MATLAB scripts, or with minor alteration.

2)Scilab: also quite compatible with MATLAB.

3)FreeMat

NOTE: [MATLAB is also available in a linux version]("http://www.mathworks.com/support/sysreq/current_release/linux.html").

For a computer algebra system, and quite powerful scripting capabilities (user defined precession etc) you cannot go past Maxima with the wXmaxima interface. This is an alternative to Mathematica and Maple. [Sage]("http://en.wikipedia.org/wiki/Sage_%28mathematics_software%29") is also quite an impressive alternative.

For classical mathematical operations, ie in numerical analysis, go for Python + Matplotlib (part of Pylab) + Numpy (numpy gives matrix operations) extensions. Fortan may also be of use in this case.

---

### Post by CalcTeX on 2009-12-20
For simply calculation for Linux could be supportive a CalcTeX, which based on the (La)TeX standard and use a python as a solver. CalcTeX user should to know part of  (La)TeX language for make a calculation, additionally is possible to include a python function, it's increase a CalcTeX possibilities. 

More info (docs & examples) on the package web side on [http://sg.bzip.pl/CalcTeX/en.html]("http://sg.bzip.pl/CalcTeX/en.html")

I recommend this package for (La)TeX's fans.
I'm author of CalcTeX and i'm open for any questions or comments, 
Regards [EMAIL="CalcTeX@onet.eu"]CalcTeX[/EMAIL]

---

### Post by muddybeemer on 2010-01-21
If you are looking for an open-source alternative to MathCad, you may want to look at CompPad: ([comppad.sourceforge.net]("http://comppad.sourceforge.net")).  Here is the description from the Sourceforge page:

"CompPad is an OpenOffice.org extension that provides live mathematical and engineering calculations within a Writer document. It is intended to provide an open-source alternative to Mathcad."

CompPad evaluates the formulas in an openoffice document and displays the results in the document.  Some of its features include:
[LIST]
[*]Units of measure
[*]Complex numbers
[*]Vectors and Matrices
[*]X-Y Plots using native OpenOffice Chart.
[*]A selection of built-in functions
[/LIST]

It is currently pre-alpha but is quite usable for basic calculations.  Check out the [CompPadDemo.odt]("http://comppad.svn.sourceforge.net/viewvc/comppad/trunk/test/CompPadDemo.odt") to see its features, and download the latest .oxt file to install the plug-in.

---

### Post by sportscliche on 2010-05-07
There is a freeware alternative to MathCad now under development primarily in Russia called SMath Studio.  It runs on Windows, Linux, and even a SmartPhone.  Homepage is here: 

[http://www.smathstudio.com/](http://www.smathstudio.com/)

and Ubuntu-specific installation instructions can be found here:

[http://en.smath.info/forum/default.aspx?g=posts&t=247](http://en.smath.info/forum/default.aspx?g=posts&t=247)

As noted, you'll need to install the Mono package to get it running.  I tried it on 8.04 and found that i) it is very primitive compared to even MathCad 5 or 6 and ii) I encountered some annoying bugs in the interface.  But hey, it's free and at the time I type this (Spring 2010) it's still brand new.  The project appears to be off to a good start.

---

### Post by dino99 on 2010-05-07
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10538](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10538)

---

### Post by BFris on 2011-03-18
Another vote for CompPad. It's really quite good. Rough around the edges, but promising enough to use for real work.

Your worksheets are self documenting because you're doing everything in a fantastic word processor. And your reports are publication quality because all equations are Formula objects and graphs are Chart objects.

---

