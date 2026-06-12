---
title: "Software for University Student"
date: 2009-08-10
forum: Education &amp; Science
---

### Post by Happyisgood on 2009-08-10
Hey!

I start my first year at University in a month or so.  I was wondering if there were any good programs you could suggest for a first year undergrad science student.

Thanks!
Happy

---

### Post by djrudra on 2009-08-10
wow...

talk about coincidences....i just logged on to ask a similar question.

could someone point me in the right direction as far as applications for scheduling studies, assignements within subjects etc.

i have checked out some of the project management apps(?) like taskjuggler and project manager etc. 

however, they seem to be for the hardcore industrial/corporate scenarios.

any help for us mere students?

much love

ananda

---

### Post by luisito on 2009-08-10
Your question sounds very general to me, so I may end up saying something totally irrelevant. My little piece of advice is that if you are going to be a science major and are eventually planning to type articles that contain a lot of math, you may want to learn how to use LaTeX. The learning curve is steep at the beginning (especially if you compare with a traditional word processor), but at the end it is the only way to type professionally looking articles in science.

---

### Post by colau on 2009-08-10
[Science]("http://ubuntuforums.org/showthread.php?t=150310")

---

### Post by Mike_IronFist on 2009-08-10
> **Happyisgood said:**
> Hey!

I start my first year at University in a month or so.  I was wondering if there were any good programs you could suggest for a first year undergrad science student.

Thanks!
Happy

Hmm...Check the "Education" section of the "Add/Remove" programs app for a bunch of programs that may or may not be relevant to your field of study.

There's lot's of calculators and stuff, as well as Science apps you might want/need.

As for general school stuff, Ubuntu already comes with OpenOffice.org, which is functionally equivelant to Microsoft Office, so you're covered there.

---

### Post by jamesrl on 2009-08-10
If I were you if you aren't writing a paper to be published in a journal (or a thesis or other very important document), would learn texmacs.  Its an extremely powerful WYSIWYG that's latex based (actually XML'd version of latex but can be converted to latex) and useful for writing scientific documents.  Much easier to type in than latex (though latex is more powerful).

Octave and maxima are good free software that somewhat mimic matlab and mathematica (which are more powerful, but cost money).  Learning python for any easy programming is also very useful (e.g., scipy/matplotlib/pylab are easy to use for scientific computational tasks).

EDIT: Also: OpenOffice (as is Microsoft office) is very difficult to write in when you are using tons of equations and want them formatted well.  Texmacs and latex are easy.  [You can probably get away with doing most homework in texmacs.]

Also if you are in the more biological or social sciences, R is very good set of statistical software.  If you get into experimental high energy physics (or similar field), you may be forced to use ROOT (root-system).  I personally think the software ROOT is very powerful, its horribly written (pretends to be C++ but it isn't, has no automatic garbage collection even in an interactive mode, fairly buggy, is named ROOT (equivalent to naming it Administrator or C:\ ), etc.).

---

### Post by CLomax on 2009-08-10
**Freemind** for mindmaps.

It's in Add/Remove.

---

### Post by sdbrogan on 2009-08-10
There are also some less well known programs you might find useful for particular tasks :
(1) Ipe - to produce diagrams with mathematical formulae (using LaTeX syntax);
(2) g3data - to read off data points from a graph image (e.g. a scanned article);
(3) GGobi - interactive visualization for multivariate data (& it integrates well with R through the rggobi package).

---

### Post by Sef on 2009-08-10
Moved to Education and Science.

---

### Post by Tibuda on 2009-08-10
It depends on what you are studing for. LaTeX is great for writing formulas and managing bibliography, and R is just the best statistical software available for any platform.

---

### Post by Happyisgood on 2009-08-10
Thanks for all the help guys.  I'll try Latex and see how long it takes me to learn! Thank you everybody for your help!

---

### Post by samden on 2009-08-10
The most important in my mind, in the order you will probably need to learn them, are:

[OpenOffice.org]("http://www.openoffice.org"):
Avoid using word processors and spreadsheets, there are better ways of doing most things, but when you need one OpenOffice does the job very well.

[Zotero]("http://www.zotero.org"):
Great reference managment software that runs in Firefox. Your uni will probably use Endnote. This does everything Endnote does and more, for free - it even has plugins for both MS Word and OpenOffice, and can export references in BibTeX format for use with LaTeX. Avoid manual reference lists, using reference management software is far more effective.

[LaTeX]("http://www.latex-project.org"): 
Far better than word processors for handling long documents - it positions all your figures automatically, does references automatically, and does all this without crashing (as Word tends to do on very long documents). To be honest you may not notice the benefits much when you are in first year and only typing short reports. But the longer your documents become, the more you will be glad you are using LaTeX. You don't want to type a dissertation or thesis in OpenOffice or MS Word, that's for sure, although plenty of poor people struggle away not knowing there is an alternative. 

There are tonnes of different programs that format documents using LaTeX, ranging from basic text editors to type directly in LaTeX code, to programs like LyX that are more like a standard word processor. Have a play around, see what you like. But my advice would be to learn to type directly in LaTeX code right from the start, it is simple when you get the hang of it and saves you having to learn it later.

[R]("http://cran.r-project.org/"):
Great statistical software. Your university may teach using SAS, GenStat or another package, and you'll need to learn these to do your courses. But you can transfer this knowledge to R, which is more powerful anyway, and you can install it on your own computer unlike the others which you'll have to go to the university computer lab to use.

When you get the hang of it, you'll be better off organising data using R instead of a spreadsheet - you'll find you hardly ever touch OpenOffice eventually.

---

### Post by ahmatti on 2009-08-11
+1 for R, Latex and Python.

---

### Post by Bucky Ball on 2009-08-11
Zotero is an excellent referencing tool. It is a Firefox add-on (Firefox->Tools->Add-on search).

Not very science-y but at uni, they're always banging on about good, consistent referencing, whatever the discipline! :)

Have fun with your studies and good luck.

---

### Post by Chronon on 2009-08-11
One more hint that isn't about a particular application: Find out what computing resources your university offers.  It pays to know what is available on the servers.  For instance, my school runs several Linux servers that students can access with their school account and run things like MatLab or Mathematica via SSH.  I can log in from a terminal and get a GUI interface to either program.

```
ssh -X username@server
```
Enter password.  Then,
```
Mathematica
```
or
```
matlab
```

Also, I can build latex documents on the server by running
```
latex document-name
```

---

### Post by samden on 2009-08-11
BTW, Zotero runs on any computer Firefox will run on, and the latest version will synchronise your references between multiple computers, whatever operating system they are using. Very, very handy.

---

### Post by Bucky Ball on 2009-08-12
> **samden said:**
> BTW, Zotero runs on any computer Firefox will run on, and the latest version will synchronise your references between multiple computers, whatever operating system they are using. Very, very handy.

Nice tip! Yes, very handy. :)

---

