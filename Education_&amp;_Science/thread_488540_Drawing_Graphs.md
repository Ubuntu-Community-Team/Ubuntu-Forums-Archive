---
title: "Drawing Graphs"
date: 2007-06-30
forum: Education &amp; Science
---

### Post by grim1234 on 2007-06-30
What does everyone use on linux to draw graphs? 

I've used excel up to now, but am looking for something to make some nice graphs for my thesis on ubuntu.

thanks!

---

### Post by akniss on 2007-06-30
You should give gnumeric a try.  The spreadsheet interface is a clone of Excel, so you should feel right at home.  The graphing takes a little getting used to, but once you figure it out it is much more configurable than Excel.

---

### Post by raja on 2007-06-30
The graphing capabilities in gnumeric are way better than excel. 
Gnumeric's advantage is that it is not a clone of excel (like ooffice calc) but is different in many ways, often for the better. The interface for making graphs is different, but is more advanced. You can create multiple plots in a chart,etc. And you can save the chart as either .svg or as .png (you choose the resolution). I also sometimes use RLplot.

---

### Post by meatpan on 2007-06-30
If you are comfortable using the command line interface, check out gnuplot.

I recently switched from R to gnuplot for graphing, and I'm astonished at how easily gnuplot can produce publication quality figures.   Keep in mind that gnuplot is very CLI oriented when you make your decision.

---

### Post by grim1234 on 2007-06-30
Excellent, thanks for the help guys! I'll try those out now.

:KS

---

### Post by crislosi on 2007-07-01
There is labplot in te repositories too

---

### Post by xadder on 2007-07-01
..and pylab/matplotlib for a more matlab type approach.

---

### Post by tkjacobsen on 2007-07-01
> **xadder said:**
> ..and pylab/matplotlib for a more matlab type approach.

I think matplotlib makes the nicest looking graphs of all software I have used...

---

### Post by dannemil on 2007-07-09
To my mind, the best and easiest to use open-source plotting package is [_RLPlot_]("http://rlplot.sourceforge.net/").

---

### Post by befana on 2007-08-10
There's a feature in Exel - when you point your mousse over the graph, you can view the x and the y values. In wich Ubuntu application I can find this feature?

---

### Post by takakia on 2007-08-14
Can Gnumeric make barcharts showing error bars?  I tried OOcalc, but it couldn't so I had to do it in excel and use the graphic in LaTeX.

---

### Post by xadder on 2007-08-14
Don't know about gnumeric, but matplotlib has this. Check out the barchart_demo.py in the examples directory.

---

### Post by xadder on 2007-08-14
In reply to befana, I'd also recommend matplotlib - it has the same feature of showing the x,y values of the mouse point.

As may be obvious by now, I like matplotlib!

---

### Post by tweedledee on 2007-08-14
> **takakia said:**
> Can Gnumeric make barcharts showing error bars?  I tried OOcalc, but it couldn't so I had to do it in excel and use the graphic in LaTeX.

Gnumeric has decent handling of error bars, much better than OO, and I think somewhat better than Excel, though not as strong as dedicated plotting programs (e.g., matplotlib).  Gnumeric also hs the advantage of very little in the way of learning curve if you're used to spreadsheets and are in a hurry.

---

### Post by befana on 2007-08-14
@ xadder Thak you for your reply. You're happy to know how to work with matplotlib!
I need to make many graphs with data from exel (it is because I want to completely remove my Windows installation, but have to make these graphs for my PhD thesis), and this data is really big amount - each graph has about 5000 rows, and fortunately, only two coloumns. Is it possible to make this with matplotlib?

---

### Post by xadder on 2007-08-14
@befana,
matplotlib (MPL) will easily handle data arrays of 5000x2. I don't know its limits, but I haven't hit them yet and I work with much bigger arrays.

I don't know how to get from excel into MPL though, as I have never needed to import from excel. This would be a job for the python script I think, and I am sure it has been solved years ago. Alternatively, exporting from excel to plain ascii (space or comma separated) should give a file which is easily loaded into python/MPL. If in doubt, a query to the MPL support list will likely give answers quickly.

I didn't know python at all until I wanted to test MPL, but I found it rather easy to learn both python (noon-style) and MPL to get things done. MPL needs a little effort, but if you want a powerful plotting framework (something like a MATLAB replacement than an excel one) then I think it is a very good choice.

---

### Post by [woodstock] on 2007-08-14
Hi xadder!

could you please post some links to tutorials that you found especially helpful for beginners (i.e. folks that know neither python nor mathplotlib).

Thank you very much.

---

### Post by xadder on 2007-08-15
Hi woodstock,

Don't need a link. Type matplotlib into google, and go to the cookbook/wiki entry. A bar plot with error bars is the 3rd example of the simple plots. (And actually, the code they give looks more complex than that in the examples directory I got with my matplotlib installation - there are many styles of working in MPL though).

The tutorial and user's guide are very good also to get the basics, although for advanced stuff and details then working through the examples directory (installed with MPL) seems to be the way to learn.

MPL does need some work, but looks like  a good long-term investment. Same as python or perl :)

I installed all of this through aptitude or synaptic on different machines. No problems that I remember.

(And I am not saying that MPL replaces gnumeric or Rlplot - all have their place and I wish I knew them all well.)

---

### Post by takakia on 2007-08-15
> **tweedledee said:**
> Gnumeric has decent handling of error bars, much better than OO, and I think somewhat better than Excel, though not as strong as dedicated plotting programs (e.g., matplotlib).  Gnumeric also hs the advantage of very little in the way of learning curve if you're used to spreadsheets and are in a hurry.

Thank you tweedledee, Gnumeric had really what I wanted(able to add standard deviation to bar charts). It was quite fast and easy too. But I had to save graphic as SVG, convert the SVG to .esp using Inkscape and includegraphics in LaTeX. Worked Well. :) .So I had no need to try Matplot.

---

### Post by nour02 on 2010-06-30
Ploticus is very good too. It's on command line.

---

### Post by mdshaver on 2010-07-02
I recommend Qtiplot. It is similar to SigmaPlot and it is much more versatile for drawing plots than Excel, Gnumeric, or Calc. It has a nice GUI so it should be pretty easy to learn re: commandline tools such as R or GnuPlot. SciDavis is almost the same thing but I prefer QtiPlot.

---

### Post by frncz on 2010-11-22
I have recently tried Qtiplot as I needed several aligned graphs and I could not do this in calc or gnumeric. Qtiplot takes a bit of learning, and it is not perfect, but in a couple of hours work I got exactly the graphs I needed.

I cut and pasted the data from calc. No problem even for 20,000 lines and five or 6 columns.

One bonus, is the 'fitting wizard'. I normally need to use Excel Solver to get the best double exponential fit to my data. Unfortunately that is not linear, so the Solver options in gnumeric or calc do not work (at least for me). The Fitting wizard in Qtiplot worked brilliantly, with good control of all parameters, fitting range etc., and provided good statistics on the fit. Brilliant.


If I could improve Qtiplot, it would be how it responds to left and right mouse clicks. It seems somewhat inconsistent and incomplete. 
For example, I can click on the axis labels to get the option to delete the axis. But if I click on the axis itself, there are no options at all.
When I have a graph with no labels, I cannot click on anything to delete it. 
There is the format menu which does allow me to do this, but it does not work from clicking on the graph.


Anyway, these are minor gripes, for a great piece of software.

Thanks to the developers

Mike

---

### Post by Moldy_Barnacle on 2010-12-01
> **meatpan said:**
> If you are comfortable using the command line interface, check out gnuplot.

I recently switched from R to gnuplot for graphing, and I'm astonished at how easily gnuplot can produce publication quality figures.   Keep in mind that gnuplot is very CLI oriented when you make your decision.

Hello,

In addition to gnuplot, as meatpan suggested, I also use TikZ/PGF -- the combined tool integrates wonderfully into LaTeX documents. The manual for TikZ is very example driven, which should get you up and running quickly. Be warned, however, that there are many typos in the sample code provided than can cause headaches if you are cutting and pasting (or killing and yanking).

Regards,
MB

---

### Post by nicolastraffic2 on 2010-12-08
with the help of excel ,  we can draw graphs.

---

### Post by Pithikos on 2011-02-23
Gnuplot is the way to go. I had to draw a graph with just having the x and y values and tried a bunch of graphical programs because I thought it would be easier. RLplot just closed everytime I told it to graph something, Lybiz can only draw already functions and not draw points. I tryied even my beloved Extcalc but its graphs are not that beautiful. I also tryied some online graphers but they seemed lacking functionality. For example one let me only give 8 points as input and not let me export the graph.
Anyhow after a lot of experimenting I said I would give Gnuplot a try. It seems it was a good choice. I did what I wanted in less than 5 minutes. There are very good short tutorials out there and the syntax is really easy to use.

So my recomendation if you are in a hurry and want a good graph, go with Gnuplot! You can learn it in less than 5 mins. I did! 8-)

---

