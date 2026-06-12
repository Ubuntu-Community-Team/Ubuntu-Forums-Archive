---
title: "Replace Matlab?"
date: 2009-03-09
forum: Education &amp; Science
---

### Post by jARLAXL on 2009-03-09
Hello everybody!

I am looking for a program that can draw my graphs charts etc. Matlab is doing that for the moment quite successfully. But since i am in ubuntu i would prefer something open source to do that.
Eventhough help function is not as good as in matlab I tried Qtoctave (yes i need a gui and if you like i can explain you the reasons) which in general looks nice and has some compatibility with matlab functions, but as i see my plots are quite ugly with gnuplot and even worse with easyplot and i even fail to install jhandles with the hope it might be better than the previous two. That is when i enter my matlab code without modifications. any other options? qmatplot? octplot? and how to install them in order qtoctave to use them to draw? Quality required: good enough for publishing the graphs in scientific literature. Optionally a good thing would be to be able to click the graphs and modify them without scripts.

Now the questions are:
1. Is it possible to get Qtoctave running (flawlessly or almost flawlessly) my matlab code (specially for drawing) or can i use another plotting program with qtoctave to do that thing? (if you reply yes i will ask which/how). Matlab compatibility is important cause i have several graphing scripts.
2. If 1 is a no then is there another program that can draw graphs and charts (not OO calc or gnumeric or kchart that do not allow me to place the axis wherever i like) easily over a GUI without need to learn a new language (such as R or Scilab)?
3. Any other suggestions? or i am better with matlab?

Thanks a lot for any help.

---

### Post by Kolmogorov on 2009-03-09
Hi,

I think your best open-source bet is to learn python and gnuplot. With these, you have a near-perfect replacement of Matlab.

Good luck!

---

### Post by favilac on 2009-03-09
Python + [NumPy]("http://numpy.scipy.org/")+ [matplotlib]("http://matplotlib.sourceforge.net/") is probably your best option.

---

### Post by jARLAXL on 2009-03-09
Thank you people for pointing at the direction.
Will check out this py stuff!:-k 
:-({|=

---

### Post by xadder on 2009-03-10
+1 for the python/matplotlib suggestion. A great part of this is ipython - lets you edit the scripts and see the result very fast. This is recommended by the matplotlib documents, and makes a good replacement for matlab.

---

### Post by iopo on 2009-03-12
I wrote some notes on using python-numpy-matplotlip:

[http://people.bu.edu/acanidio/opensource.html](http://people.bu.edu/acanidio/opensource.html)

it is not a tutorial but it explain what they are from a Matlab user perspective. Good luck!

---

### Post by lvleph on 2009-03-12
You know, I just thought of a way to be able to be able to get octave to run most matlab code. What one could do is take all the matlab functions and import them into octave. I am sure this would not get everything to work, but I bet a lot of it would work. I have not tried this, but...

---

### Post by eldragon on 2009-03-12
you could try sage, but i found it quite confusing. maybe if i knew python...

---

### Post by perroazul on 2009-03-24
> ** said:**
> 1. Is it possible to get Qtoctave running (flawlessly or almost flawlessly) my matlab code (specially for drawing) or can i use another plotting program with qtoctave to do that thing? (if you reply yes i will ask which/how). Matlab compatibility is important cause i have several graphing scripts.
hi, 
I tried running my most important matlab scripts with octave a few months ago, and all of them worked flawlessly. some of them are fairly sophisticated, e.g. for reading binary data from external files for drawing surfaces, etc or others for making animations. The only difference was in the execution time. it took much longer in octave, say an increase from two seconds to 40 seconds.

---

### Post by neoflight on 2009-03-28
octave + gnuplot..if you are using basic matlab functions, there is almost complete compatibility between octave and matlab. you can just run .m files.

---

### Post by vhegos on 2009-03-28
I have been using a combination of gnuplot and python for all my plotting needs for a while now.  There is also a module called gnuplot.py which essentially lets you control gnuplot using python.  It may seem a bit far afield to learn some python just to make plots, but probably you will thank yourself later.  Python is a handy tool to have.

On a related note, what sort of output format do people like to use when combining gnuplot and latex?  I typically set the output to be latex code, but sometimes it seems that there has to be an easier way.  Any thoughts?

---

### Post by xadder on 2009-03-29
+1 for python+matplotlib+numpy - much better graphics than gnuplot in my view, and even better quality than matlab. Search for matplotlib to get to the great documentation pages ad gallery.

---

### Post by ad_267 on 2009-03-29
You can also try exporting your data to text files from octave and then plot the data using gnuplot. You should be able to customise your plots a lot more easily that way and get them looking how you'd like.

If you don't need to worry about Matlab compatibility, then Python+SciPy+MatPlotLib is a really good way to go. For 3D plotting the options aren't as good however, I've only found MayaVi. Anyone have any tips for 3D plotting?

> **vhegos said:**
> On a related note, what sort of output format do people like to use when combining gnuplot and latex?  I typically set the output to be latex code, but sometimes it seems that there has to be an easier way.  Any thoughts?

Thanks for the gnuplot.py hint.

I don't have a lot of experience using gnuplot with LaTeX yet but I've found using the epslatex terminal in gnuplot works well. Then I use eps2pdf on the eps file (for use with pdflatex) and include the tex file from my LaTeX document. I had to use "\graphicspath{{img/}}" to get this working with plots in a separate directory.

---

### Post by meborc on 2009-03-29
i wonder why [Scilab]("http://www.scilab.org/") has not been mentioned in this thread... there are minor differences between matlab and scilab, but mostly it is fantastic

;)

---

### Post by grj23 on 2009-09-09
Definitely python + numpy/scipy + matplotlib.  In my opinion this more than replaces matlab - more powerful and somehow just great fun.  

Python is the only coding language I've heard off where people "fall in love".  It's quite extraordinary.  See, for example [http://xkcd.com/353/](http://xkcd.com/353/)

I spent a long time pre-ubuntu, converting myself to open-source.  I tried Octave as the "obvious" replacement for MatLab, and fiddled around with a few other things, (Java, R).  Eventually I gave python a hesitant try and never looked back.  

Regarding the format for use in LaTeX, I typically try to do .eps, or .png.

---

### Post by XCan on 2009-09-09
Why ever export to .png though? Noone likes pixelated figs. :p

---

### Post by ahmatti on 2009-09-09
> **XCan said:**
> Why ever export to .png though? Noone likes pixelated figs. :p

There is no need to use png and you shouldn't! Use eps or pdf, (eps does not work with pdflatex). 

As for Matlab replacement I'd also go with Python, using Spyder as IDE [http://code.google.com/p/spyderlib/](http://code.google.com/p/spyderlib/).

---

### Post by ad_267 on 2009-09-10
> **ahmatti said:**
> There is no need to use png and you shouldn't! Use eps or pdf, (eps does not work with pdflatex).

You can use the eps2pdf program to convert eps to pdf though.

---

### Post by meborc on 2009-09-10
> **ahmatti said:**
> There is no need to use png and you shouldn't! Use eps or pdf, (eps does not work with pdflatex). 

As for Matlab replacement I'd also go with Python, using Spyder as IDE [http://code.google.com/p/spyderlib/](http://code.google.com/p/spyderlib/).

eps WILL work with pdflatex soon

> TeX Live 2009 (to be released soon) includes a new version of the epstopdf package which performs on-the-fly conversion of EPS files when compiled with pdfTeX

quote taken from TexWorks mailing list

---

### Post by XCan on 2009-09-10
Wow, that will be nice. :) It will absolutely save me some work on the exporting front in the future.

---

### Post by eRoot on 2009-09-10
I'm looking into python, together with numpy, scipy and matplotlib, seeing some of the recommendations here.

I'm wondering if this configuration is capable of curvefitting, confidence bands and those sort of things. I did see a least square function for non-linear fitting, but I can't find any other features. Now, I don't need every statistical feature known to mankind, but as a physics student I do need the tools to properly analyse experimental data.

---

### Post by XCan on 2009-09-10
Speaking of non-linear optimization, lsqnonlin is a joke anyway in Matlab*, if it exists in one of those packages, I'm curious how well it works. 

*By joke, I mean slow as heck. Self implementation doesn't take too long and yield far better performance since it can be honed to the problem of interest.

---

### Post by engelp on 2009-11-26
> **ahmatti said:**
> There is no need to use png and you shouldn't! Use eps or pdf, (eps does not work with pdflatex). 

As for Matlab replacement I'd also go with Python, using Spyder as IDE [http://code.google.com/p/spyderlib/](http://code.google.com/p/spyderlib/).

Hi, since you have to import those libraries in the script, why do you sugest using an ide? And what about alternatives to spyder? I have read about sage and eclipse with pydev puglin can make any suggestion?

thanks

---

### Post by ahmatti on 2009-11-27
**@engelp** I prefer to use an IDE for interactive data analysis before I make a script out of the whole thing. Or if I just wan't to do some exploratory plotting etc. Of course don't need to use and IDE for that and a lot times I just use "Ipython -pylab".   

Spyder provides an environment very similar to Matlab, which is why I suggested it as a Matlab replacement. Its really up to your personal preference, I sometimes use Geany or Emacs too.

---

### Post by Alexandre Putt on 2009-11-29
I prefer using R for producing high quality charts.

---

