---
title: "learn python for scintific computing?"
date: 2007-01-19
forum: Education &amp; Science
---

### Post by timmie on 2007-01-19
Hello!

does anyone know a good website with a nice python tutorial which is tailored to scientific analysis?

I am doing natural sciences and did not really study programming nor computer science. Thus I am finding it very difficult to learn basic programming which then could help me a lot in doing my research work.

I read the SciPy and NumPy cookbook but still can't get more things to work than running the examples...

In the meantime it is very obvious for me now that knowing some Python tricks my analysis would be more effective.

Thanks for any hints or suggestions.

---

### Post by meng on 2007-01-19
What sort of analysis did you have in mind? Statistics? Graphs?

---

### Post by timmie on 2007-01-19
descriptive statistics and numeric analysis.

But yes, all is then directed towards plotting the results on maps or diagrams.

For instance let's say one has  a text file with values logged by a measurement device and wants do display these as histograms.
Also I need to do interpolation between my data points.

---

### Post by Patsoe on 2007-01-19
I just bought this book, but for now I can only tell you that at least the first two chapters are pretty good reading :)

[http://www.springer.com/sgw/cda/frontpage/0,11855,1-40109-22-83511316-0,00.html](http://www.springer.com/sgw/cda/frontpage/0,11855,1-40109-22-83511316-0,00.html)

---

### Post by LaserJock on 2007-01-20
> **Patsoe said:**
> I just bought this book, but for now I can only tell you that at least the first two chapters are pretty good reading :)

[http://www.springer.com/sgw/cda/frontpage/0,11855,1-40109-22-83511316-0,00.html](http://www.springer.com/sgw/cda/frontpage/0,11855,1-40109-22-83511316-0,00.html)

I got this book from the uni library and it's what really got me going with Python. Some of it is a tad outdated (as many computer related books are) but it was definitely helpful for me. I also recommend looking at [scipy]("http://www.scipy.org") and [matplotlib]("http://matplotlib.sourceforge.net/") . They are both in the repos and are pretty cool for scientific uses.

-LaserJock

---

### Post by timmie on 2007-01-20
Hi!

It's nice to see that there are others struggeling into Python ):P 

I find some links yesterday which I think are nice.

[LIST]
[*][http://wiki.python.org/moin/NumericAndScientific](http://wiki.python.org/moin/NumericAndScientific) => links to numeric-related things
[*][http://www.scipy.org/wikis/topical_software/Tutorial](http://www.scipy.org/wikis/topical_software/Tutorial) => this is a very good tuturial and somehow for what I was looking. You can download sample data and a PDF
[*]For those of you already familiar with IDL [http://www.johnny-lin.com/cdat_tips/](http://www.johnny-lin.com/cdat_tips/)
[/LIST]

About the book:
I will certainly have a look. The O'Reilly "Lerning Python" is not very ditactical and maybe only useful for programmers...
I think I saw the book already on some pages but was deterred by the term "computional science". Having taken a closer look it looks certainly interesting :-\" 

Greetings,
Timmie

---

### Post by tweedledee on 2007-01-20
> **timmie said:**
> descriptive statistics and numeric analysis.

But yes, all is then directed towards plotting the results on maps or diagrams.

For instance let's say one has  a text file with values logged by a measurement device and wants do display these as histograms.
Also I need to do interpolation between my data points.

Honestly, unless you are doing high performance computing and/or massive quantities of data (billions of data points), I'd stay away from numeric, numpy, & scipy - they are very powerful, but hard to learn and overkill for a great many tasks - and some of the routines appear broken with the last few releases of python.  While I can't suggest a particular text (I taught myself python years ago), I highly recommend the tutorial in the standard python documentation, and approach the problem step-wise.  For example, to interpolate data points, you need to (at least one solution):
a) open a file for reading
b) read in the data points
c) for each pair of points, generate an intermediate data point and store it
d) write out the resulting list of points

The nice thing about python is that how to do all of that is in the tutorial.  You can find how to open, read, and write files in the section on file handling, and the rest of it is just list processing (which the tutorial has many examples of) plus some basic arithmetic.

Obviously more complicated problems require more sophisticated solutions, but you can do an amazing amount simply by tweaking a few examples found in the tutorial.  Many other specific tasks have examples that turn up via a Google search.  And a good, basic python book would probably help.

---

### Post by entropic_existence on 2007-01-20
If you want to do statistical anaylsis and plotting of your data I would highly recommend learning how to use R, which is a free statistics package much like S+, SAS, etc. It isn't really a programming language in the sense of Python, Perl, C, etc but has many similarities and its own syntax. Very powerful with a ton of packages and plug-ins for particular needs.

---

### Post by timmie on 2007-01-20
Hi!
Thanks to tweedlede and entropic_existence for their hints not to complicate thinks.

Well again, the problem is more to find a starting point. and for a natural scientist the "real world"-problem is the motivation and not to program another python text editor or whatsoever.
I was just impressed by the programs a colleague of mine writes in IDL to solve problems for which I'd use hours with text editors, spreadsheets and information systems.
So it's all about increasing efficiency. At least after having learned a some basic knowledge.

I am thinking of python instead of R (which I have been using already during one assignment) because it provides more flexibility.
With Python I'd be able to access R ([http://rpy.sourceforge.net/)](http://rpy.sourceforge.net/)), C, Fortran...
It'd also help me pubishing my results on the web.

That's what I see so far...

---

### Post by neoflight on 2007-01-22
has anyone succefully wrapper a fortran hpc with python for GUI? ..
i do not wish to use Qt for GUI...may be wxpython is a good option....

it would be great if someone could post a sample code or link to somewhere....

i want to have the UI responsive enough such that the use can input values...and carry one with the execution if there is no input for a particular time interval...similar to the grub booting from the default after a timeout...

any experience in that sorta thing?

---

### Post by slaanco on 2007-01-23
> **timmie said:**
> descriptive statistics and numeric analysis.

But yes, all is then directed towards plotting the results on maps or diagrams.

For instance let's say one has  a text file with values logged by a measurement device and wants do display these as histograms.
Also I need to do interpolation between my data points.

for making graphs use gnuplot that§s the best tool, you can even make gnuplot to make your graphs in real-time as the values from some apparatus change with time.

i'm writing most of my "programs" in C, it's easy to learn, then you can could transfer to python easier. try it ;)

---

