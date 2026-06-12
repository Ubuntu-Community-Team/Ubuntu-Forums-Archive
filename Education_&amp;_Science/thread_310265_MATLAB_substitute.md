---
title: "MATLAB substitute"
date: 2006-11-30
forum: Education &amp; Science
---

### Post by pillu on 2006-11-30
Hi all

I am pursuing my PhD in electrical engineering and use MATLAB quite a bit. I was looking for substitutes to install on my home computer. It seems that I have two options - Scilab and Octave. 

Which one is the most easy to switch to from MATLAB ? I would love to use an open source software but do not want to spend the time to learn a whole new language. Any tips ?

---

### Post by slimdog360 on 2006-12-01
octave, make sure you also install the octave-forge package. Pretty much all the commands are the same except for a few plotting commands. You will also need the gnu-plot package to plot with octave, this is why there is a difference in some of the plotting commands.

Scilab goes about things in a different way and as such many of its commands are different also. This is not to say its worse, you may as well find that Scilab is better then Matlab its self, but if you want compatability go with Octave.

---

### Post by aysiu on 2006-12-01
Isn't there a native Linux Matlab...?

---

### Post by slimdog360 on 2006-12-01
> **aysiu said:**
> Isn't there a native Linux Matlab...?
yeah, but he wanted something open source and Im guessing something free.

---

### Post by emix on 2006-12-01
Scilab has this tool:

[Matlab to Scilab Translator]("http://www.scilab.org/doc/demos_html/node264.html")

---

### Post by pillu on 2006-12-01
> **aysiu said:**
> Isn't there a native Linux Matlab...?

Yeah there is...but it isn't free...I guess I should try my hand at something free before paying for MATLAB

---

### Post by Jbloudg20 on 2006-12-01
Check at your bookstore. I was able to purchas Matlab for liek $50. It was well worth it IMO.

---

### Post by neoflight on 2006-12-01
> **slimdog360 said:**
> octave, make sure you also install the octave-forge package. Pretty much all the commands are the same except for a few plotting commands. You will also need the gnu-plot package to plot with octave, this is why there is a difference in some of the plotting commands.

Scilab goes about things in a different way and as such many of its commands are different also. This is not to say its worse, you may as well find that Scilab is better then Matlab its self, but if you want compatability go with Octave.

is there a builtin editor for octave? if not how do i make the code in text file and run ? i mean something like the matlab editor? thanks

---

### Post by alancaerdydd on 2006-12-01
> **Jbloudg20 said:**
> Check at your bookstore. I was able to purchas Matlab for liek $50. It was well worth it IMO.

I suspect that that is the student version. If I remember rightly it's exactly the same except that all graphs have a banner on them saying Matlab Student version. I don't think it's easy (or legal) to remove that which is awkward for PhD/publication stuff. However, probably quite simple to interface with gnuplot to graph arrays.

Haven't had time to look at Octave yet, does it have a function comparable to simulink for quick building of models?

---

### Post by slimdog360 on 2006-12-02
> **neoflight said:**
> is there a builtin editor for octave? if not how do i make the code in text file and run ? i mean something like the matlab editor? thanks

I use koctave and use the text editor with that. I think there is also a new frontend for octave running around somewhere but I cant remember what its called.

---

### Post by adamkane on 2006-12-03
It's called octave-workshop, and it's too difficult to install on Ubuntu:
[http://www.math.mcgill.ca/loisel/octave-workshop/](http://www.math.mcgill.ca/loisel/octave-workshop/)

Score one more for Fedora.

---

### Post by neoflight on 2006-12-04
i actually found out recently that i can use any editor and save the file as something.m and run that file like that in matlab; just use the filename with out extension. if the file doesnt have any extension then run as 

```
> source "something" 
``` with quotes.


so gedit is fine with me... :D

---

### Post by roderikk on 2006-12-04
Yep, and gedit of course has native .m file code highlighting so that works perfect!

To get a hang of all the plotting with gnu plot you might want to check out this site: [http://t16web.lanl.gov/Kawano/gnuplot/plot1-e.html](http://t16web.lanl.gov/Kawano/gnuplot/plot1-e.html)

---

### Post by tkjacobsen on 2006-12-04
> **neoflight said:**
> is there a builtin editor for octave? if not how do i make the code in text file and run ? i mean something like the matlab editor? thanks

In gedit you can also add an external tool, which is running the script in octave - then closing..

---

### Post by adamkane on 2006-12-05
You can enter data in TeXmacs (MATLAB style), and TeXmacs will display the solutions as well:
[http://www.texmacs.org/tmdoc/plugins/octave/octave-main.en.html](http://www.texmacs.org/tmdoc/plugins/octave/octave-main.en.html)

Thanks for the gnuplot link.

TeXmacs does gnuplot as well. Load the gnuplot session, enter the Section 4. Graph Gallery Examples, then press enter:
[http://www.texmacs.org/tmdoc/examples/casdoc.en.html](http://www.texmacs.org/tmdoc/examples/casdoc.en.html)

---

### Post by venik212 on 2007-01-06
Is Octave currently being developed/debugged/extended?

---

### Post by tkjacobsen on 2007-01-07
Yes. they released version 2.9.9  on october 2, 2006  - which will soon replace the testing version 2.1.73, and their mailing lists are very active.

---

### Post by WebDrake on 2007-01-07
The one really outstanding issue is graphics.  Octave's object-oriented plotting model still does not match the capabilities of MATLAB.  It is still possible to achieve good plots, just not as easy as one might like.

I think this will be fixed soon, but probably not as soon as we'd hope for.  I recall from some mailing list debate that it is likely to not be fully implemented in the soon-to-be-released 3.0, but should come in an update to that.

---

### Post by Jbloudg20 on 2007-01-08
I attpempted to install octave workshop, ad it was a nightmare. 

If only fedora wasn't such a PITA for simple stuff, I'd probably make a permanent switch.

---

### Post by fadder on 2007-01-09
matplotlib seems to provide quite good graphics, with MATLAB-style functions, but from a python environment.

I have just started testing this, but the combination of numpy (to get some nice array functionality) and ipython seem to work great.

---

### Post by vinx on 2007-04-20
It was no nightmare at all to install the workshop: [http://ubuntuforums.org/showthread.php?t=150310&page=5#42]("http://ubuntuforums.org/showthread.php?t=150310&page=5#42")

So give another try!

---

### Post by eneth80 on 2007-10-19
>It was no nightmare at all to install the workshop: >[http://ubuntuforums.org/showthread.p...0310&page=5#42](http://ubuntuforums.org/showthread.p...0310&page=5#42)

when i do ./configure 
I get:
..
checking does moc work?... yes
checking can I compile moc_myqt.cpp?... configure: error: couldn't compile moc_myqt.cpp

---

### Post by Argus on 2007-10-19
They is also SAGE [http://www.sagemath.org/](http://www.sagemath.org/)

---

### Post by mattflaschen on 2008-08-29
> **eneth80 said:**
> >It was no nightmare at all to install the workshop: >[http://ubuntuforums.org/showthread.p...0310&page=5#42](http://ubuntuforums.org/showthread.p...0310&page=5#42)

when i do ./configure 
I get:
..
checking does moc work?... yes
checking can I compile moc_myqt.cpp?... configure: error: couldn't compile moc_myqt.cpp

On my Gutsy system, I fixed this by running:

sudo update-alternatives --config moc

and choosing qt4.

Of course, this will probably break something later and I'll have to change it back.

---

