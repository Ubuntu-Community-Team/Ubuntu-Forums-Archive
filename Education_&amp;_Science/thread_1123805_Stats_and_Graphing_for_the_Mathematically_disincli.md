---
title: "Stats and Graphing for the Mathematically disinclined"
date: 2009-04-12
forum: Education &amp; Science
---

### Post by mdshaver on 2009-04-12
I was wondering what the best programs to use for those social, behavioral, and heath researchers who have a weak math and computer science background.

I am a PhD student in audiology and am using OpenOffice as my word processor with Bibus as my referencer. This combo seems to be workin good so far.

For stats, I have installed OpenStat through Wine which seems like a great alternative to SPSS. PSPP has a nice interface but is far too limited. The R GUI, RKWard, looks nice but it just doesnt seem quite as intuitive for persons with an SPSS background.

For graphing, I have been using OpenOffice. I may try Gnumeric but I'm guessing its graphs will look about the same. I liked RLPlot but it is kinda buggy. I havent had time to fully explore Grace yet. 

I realize that programs like R and GnuPlot are superior for those that are proficient with them but I am more interested in hearing about experiences with programs that have nice, intuitive GUIs.

Any thoughts or comments?

---

### Post by Gilabuugs on 2009-04-13
It is really hard to make graphs with a gui (you pretty much have to enter programming input of some sort) unless your using a spreadsheet program in my opinion, gnuplot is really easy to learn (the basics) I know windows has a gui for it but its basically the same as the command line you get in linux.

Your best bets are probably OOo calc or gnumeric, though I don't have experience with many gui software

I'm surprised you get away with using openoffice writer rather than \LaTeX\ :)

---

### Post by euler_fan on 2009-04-13
For better or worse there's a tradeoff between control and ease of use.

A speadsheet program (if it can graph what you want . . . might be a big if) is probably the `easiest' or at least the most gui'ed plot maker.

On the other end is R or gnuplot where you pretty much have total control but need to learn a little command line.

---

### Post by mdshaver on 2009-04-13
Thanks for the responses so far!

Anyone have any experience with Grace, RLPlot, or OpenStat? Any comments/complaints about these programs?

---

### Post by gunksta on 2009-04-13
> **mdshaver said:**
> I was wondering what the best programs to use for those social, behavioral, and heath researchers who have a weak math and computer science background.

As a research consultant who specializes in social and behavioral research, it always scares the @#$% out of me when I see people looking for stats software for those who have a weak math background. I do _not_ expect social researchers to be closeted computer scientists, but I think it's easy to jump to the other extreme as well. In my areas of expertise (childhood development, child welfare, elder care, etc.) I have read more than one paper where the researcher made some bold claims, but the mathematical methodology made me question the validity of their claims. Unfortunately, these papers were all published in respected peer-reviewed journals. 

> **mdshaver said:**
> I am a PhD student in audiology and am using OpenOffice as my word processor with Bibus as my referencer. This combo seems to be workin good so far.

For stats, I have installed OpenStat through Wine which seems like a great alternative to SPSS. PSPP has a nice interface but is far too limited. The R GUI, RKWard, looks nice but it just doesnt seem quite as intuitive for persons with an SPSS background.

I've not (yet) used OpenStat, so I won't comment on something I know practically nothing about. Depending on the nature of the statistics you may need to run, it is possible that a spreadsheet program such as OpenOffice.org or Gnumeric may very well be an appropriate tool. MS Excel had some famous problems with certain statistical formulas, but the problems generally affected very very large and very very small numbers, not the kinds of numbers often used by social researchers at least. For most of us, spreadsheets are more than accurate enough.


> **mdshaver said:**
> I realize that programs like R and GnuPlot are superior for those that are proficient with them but I am more interested in hearing about experiences with programs that have nice, intuitive GUIs.

Any thoughts or comments?

I try to be software agnostic. I try to use the "best" tool for the job, understanding that "best" may be subjective. If all I need to do is build some cross-tabs with a relatively small data set and present a few tests for independence, I may just use a spreadsheet. Remember, there are two parts to our job. First, we need accurate numbers AND we need to effectively communicate our findings to others. Spreadsheets often suffice for the first requirement and they excel (pun intended) at the latter.

The knee-jerk suggestions for plotting on GNU/Linux are all very nice (gnuplot, etc.) but are generally unnecessary. Here's a newsflash - you can get nice plots from OOo or Excel. We use them ALL the time and our clients are typically state and county governments. The _real_ disadvantage is in reproducibility and adaptability. To me, Calc is adequately flexible, but it can be slow to use when I need to make lots of graphs. Spreadsheets tie you to a GUI. If I have a data set in a spread sheet and I need a couple of quick charts, I'll probably just use Calc. If I need MANY graphs, I dump Calc and drop down to the command-line to use more powerful tools. These tools aren't necessarily better and for one or two graphs they may very well take longer. But, when I need to produce a couple dozen graphs in a single afternoon, the advantages of a programmable tool are hard to argue with. 

There is another trend that I think will become increasingly important for social scientists. Many social scientists and government (US) systems rely on "flat-file" datasystems. An example of this classical pattern is the AFCARS "database" that tracks the progress of children in foster care. These legacy systems are slowly being replaced with more modern relational database systems, which is a good thing.

In the realm of social/behavioral research I think there should be more training/education for people earning masters and PhD level degrees with an interest in research. PSPP will, over time, catch up with SPSS. R has more than enough power for anything I'll ever need to do and Postgres/MySQL/SQLite are all great databases. With the exception of R, these all come with a user interface (of some sort).

I think the solution is more training and education, not new tools.

---

### Post by skintythe1andonly on 2009-04-13
I personally use latex for all my stuff, papers, posters and presentations, and use jabref to manage my references. I'm studying physics though so need it for equations.

For graphs I use mathematica but understand you are looking for a free alternative.

Origin is used in our department a lot for plotting data, but have found qtiplot very similar and a very good free alternative

---

### Post by hubie on 2009-04-13
> **gunksta said:**
> As a research consultant who specializes in social and behavioral research, it always scares the @#$% out of me when I see people looking for stats software for those who have a weak math background. I do _not_ expect social researchers to be closeted computer scientists, but I think it's easy to jump to the other extreme as well. In my areas of expertise (childhood development, child welfare, elder care, etc.) I have read more than one paper where the researcher made some bold claims, but the mathematical methodology made me question the validity of their claims. Unfortunately, these papers were all published in respected peer-reviewed journals. 

I have to agree.  Things like statistics and probability analysis can be confusing and easy to trip up even for people who should know better.  You really have to have a good feel for the data before you start an analysis.  For example, if you're not reasonably confident that your data consist of statistically independent events, you can really get into trouble throwing the "usual" analysis tools from a software package at it.

I don't know how common it is, but when I was in grad school, the math department offered free statistical consulting to anyone, particularly for those working on their dissertations.  My guess is that it was their way of training their grad students.

> **gunksta said:**
> Here's a newsflash - you can get nice plots from OOo or Excel. We use them ALL the time and our clients are typically state and county governments.

This is probably a personal preference thing, but in general I would have to disagree, at least for Excel (I very seldom use OOo to make graphs).  I find the default Excel graph to be very ugly, and at times, hard to decipher (even when I make them myself).  The appeal is that you can make graphs very quickly in Excel, and I will do this myself at times if I want a quick look at data, but it falls way short (in my opinion) for creating publication-quality charts.  I find that plot area is too easily sacrificed to title, subtitle, and axis label space whereby the data become secondary to the data labeling.  I also have a lot of other issues with it that I won't go into.  Most of the issues that I have, I'm sure, can be solved by spending the time to change and tweak a bunch of values (axis ranges, font sizes, symbol types, line types, etc., etc., etc.), but by the time it takes me to screw around with all that, I can have a very nice looking plot done up in R, plus have a very handy script available to regenerate it or make anew with new data.
> **gunksta said:**
> 
In the realm of social/behavioral research I think there should be more training/education for people earning masters and PhD level degrees with an interest in research.

Unless my experience with coming up through the physical sciences was unique, I would say the same for the physical sciences as well.  We were taught many mathematical techniques for solving theoretical problems, such as boundary value problems, but we were given very little instruction in data analysis.  You usually ended up learning it when you started generating your own data and you had to start muddling through it yourself.

As a funny example, I know of one case where a student was presenting a thesis defense where a graph was shown with two data points that were measured.  The next graph was the same data plot with an empirical model overlaid on it that showed very good agreement between model and data.  The empirical model that fit the two data points so well was a high order polynomial. :)

---

### Post by mdshaver on 2009-04-13
I don't disagree that it is important to have more than a superficial understanding of statistical application before analyzing a dataset; however, this understanding and proficiency with the command line and languages such as R or S do not necessarily go hand in hand. Although I do feel that I am rather weak in this area as I am still a student, I feel comfortable in pointing out that commercial stats and graphing programs which use GUIs are the norm, not the exception. It is apparent that although powerful and free applications such as R and GnuPlot may be a godsend to some it seems highly unlikely that they will be adopted by the masses who may be more comfortable using SPSS and Sigmaplot or similar programs. However in the linux world, there is no need to reiterate how wonderful and powerful these programs are because these opinions are abundant when googling "linux" and "statistical programs". My main interest was in getting feedback from researchers and students who had experience with some of the GUI-based programs (including spreadsheets) and what your thoughts on the advantages and disadvantages are for said programs. 

Thank you for all your responses so far.

---

### Post by gunksta on 2009-04-13
The most advanced FOSS statistical package with an integrated GUI is PSPP/PSPPIRE. Rkward is a front-end for R, but it's development may be and writing a GUI for R is a little like putting a tow package on a Ferrari.

Unfortunately, PSPP is not feature complete. For many of us, it is not adequate. However, I think PSPP is incredibly important because it copies the layout of SPSS so perfectly. As PSPP becomes more feature complete, users with experience using SPSS will increasingly find it to be a competent alternative. Hopefully the next version, rumored to be 0.7, will include an updated output engine and will be a better candidate for showing people who are interested in using Linux but need point and click statistics.

---

### Post by earlycj5 on 2009-04-14
There's always SAS JMP for Linux.  It offers a point and click interface that you seem to desire.

SAS offers a free 30 day trial to see if you like it.  I've used it before just for kicks, but stick with R.

---

### Post by gunksta on 2009-04-15
I installed OpenStat. I created a simple, fake dataset and played around with it. It's UI seems pretty friendly and easy to use.

---

### Post by hzambran_cl on 2009-04-16
> **mdshaver said:**
> It is apparent that although powerful and free applications such as R and GnuPlot may be a godsend to some it seems highly unlikely that they will be adopted by the masses who may be more comfortable using SPSS and Sigmaplot or similar programs.

I disagree with this opinion, and for supporting my disagreement, I would suggest to read the following articles on the New York Times:

[http://www.nytimes.com/2009/01/07/technology/business-computing/07program.html]("http://www.nytimes.com/2009/01/07/technology/business-computing/07program.html")

[http://bits.blogs.nytimes.com/2009/01/08/r-you-ready-for-r/]("http://bits.blogs.nytimes.com/2009/01/08/r-you-ready-for-r/")

Obviously, at the end anyone is free to choose the "*best*" tool for a particular job (citing part of the nice '**gunksta**' message), and free to define what "*best*" means for himself...

---

### Post by ahmatti on 2009-04-23
For easy plotting of data and simple curve fitting see kst [http://kst.kde.org/](http://kst.kde.org/)

---

### Post by BramWillemsen on 2009-04-23
I've always used xmgrace for plotting. It's quite a wonderful tool and not too hard to learn. I've always used similar types of input so i maybe not be too familiar with all the options of the program, but for plotting its absolutely amazing. i always used two column output files (x,y). You take these as input and xmgrace plots it for you. You can use as many input files as you want in the same graph.

You can adjust colours, symbols for each point and many other options. The output looks pretty neat too. I'm currently working on my bachelor scription and these two figures show some of my model output. Turning model output into figures is really easy by killing the previous data and inserting data from new 2-column files. All the settings like labels and axes remain the same then. 

[http://i35.photobucket.com/albums/d174/Brasempje/figure3temp.png](http://i35.photobucket.com/albums/d174/Brasempje/figure3temp.png)
[http://i35.photobucket.com/albums/d174/Brasempje/figure6temp.png](http://i35.photobucket.com/albums/d174/Brasempje/figure6temp.png)

Hope this helps you a bit.

---

### Post by sdbrogan on 2009-05-01
I hadn't heard of OpenStat, so decided to have a dekko.  I tried multiple regression on the Longley test data (a tricky case that can cause weak algorithms to fail) & checked the results against those certified by NIST; in short it gave the wrong answers. Did you notice when you start it up you're warned "You should attempt to verify the accuracy of results with hand-calculated examples or other data of known solution" ?  It's a nice piece of software, & could be handy for students, but it's surely not the substitute for SPSS for researchers you asked for.
I think your options are (1) buying SPSS (it's available for Linux OSs), (2) waiting for PSPP to have all the functionality you need, or (3) using R (which passes the Longley test of course).
I don't think the difficulty of using R should be exaggerated.  Even using it from the command line any common test can be carried out in one command - it's a high-level language. Cut & paste from a crib sheet if you don't use it often enough to remember the syntax. R Commander is another GUI front end you could try if you don't like RKWard - it's not particularly swish, but as easy to get the hang of as any other GUI.
The Longley data is at
[http://www.itl.nist.gov/div898/strd/lls/data/Longley.shtml](http://www.itl.nist.gov/div898/strd/lls/data/Longley.shtml)

---

### Post by macotto on 2009-05-02
A speadsheet program (if it can graph what you want . . . might be a big if) is probably the `easiest' or at least the most gui'ed plot maker.

---

### Post by sdbrogan on 2009-05-05
By the way, PSPP also gives the right answers for this regression.

---

### Post by lethalfang on 2009-05-06
> **mdshaver said:**
> I was wondering what the best programs to use for those social, behavioral, and heath researchers who have a weak math and computer science background.

I am a PhD student in audiology and am using OpenOffice as my word processor with Bibus as my referencer. This combo seems to be workin good so far.

For stats, I have installed OpenStat through Wine which seems like a great alternative to SPSS. PSPP has a nice interface but is far too limited. The R GUI, RKWard, looks nice but it just doesnt seem quite as intuitive for persons with an SPSS background.

For graphing, I have been using OpenOffice. I may try Gnumeric but I'm guessing its graphs will look about the same. I liked RLPlot but it is kinda buggy. I havent had time to fully explore Grace yet. 

I realize that programs like R and GnuPlot are superior for those that are proficient with them but I am more interested in hearing about experiences with programs that have nice, intuitive GUIs.

Any thoughts or comments?

You can try GNU Octave along with its GUI frontend QtOctave. The two are designed to be compatible with MATLAB, which is a very powerful numeric program. It makes nice graphs and stuff.... don't know if it fits your needs.

---

### Post by nanonils on 2009-05-08
Unfortunately, I will have to use JMP8 to share files with collaborators. Because I'm still fairly new to Linux I have a question regarding the installation location: should that be /home or /opt as suggested by JMP8?

I am the administrator of my computer and occasionally would like to do a clean Ubuntu install, keeping /home on a separate partition. 

Is it OK to follow the default location and then just copy this back or would you simply install it on /home? Will links break after a clean install?

---

### Post by gunksta on 2009-05-11
> **nanonils said:**
> Unfortunately, I will have to use JMP8 to share files with collaborators. Because I'm still fairly new to Linux I have a question regarding the installation location: should that be /home or /opt as suggested by JMP8?

I am the administrator of my computer and occasionally would like to do a clean Ubuntu install, keeping /home on a separate partition. 

Is it OK to follow the default location and then just copy this back or would you simply install it on /home? Will links break after a clean install?

nanonils: If this doesn't answer your question, consider starting a new thread. You'll probably get more help that way. I've never used JMP 8, but your questions are pretty generic.

I would install JMP 8 to /opt, as per the directions. I don't like to have executable in my home directory. If you do choose to install to /home, I would recommend doing the installation that way up front. Copying _could_ break links, depending on how the installer works.

The reason I recommend /opt is because clean installs are rarely necessary with Ubuntu. (although they can be fun.) If you do a clean install, you might as well reinstall JMP 8 too. It shouldn't take that long. The big risk with stuff like JMP 8, is that in the future you could have problems with things like libc. Open source programs, like R, PSPP, etc. are recompiled for each Ubuntu release with the latest and greatest system libs, graphical toolkits, etc. JMP 8 is not, since it is proprietary. It is, in effect, stuck in time like a fossil. If something that JMP 8 depends on changes dramatically (breaks API/ABI compatibility) it may not work in the future. I recommend that you have a non-critical test-machine so you can test upgrades or you could upgrade and "break" JMP 8 without meaning to.

---

### Post by samden on 2009-05-16
I am just finishing my PhD (should be handing in my thesis within a week, all going well...) so your situation is very familiar to me.

When I started out I was just like you - typing everything in Word, graphs in Excel, had minimal knowledge of statistics.

I plodded on for the first year like that, but soon found that if you try to type a thesis in Word (or OpenOffice) you spend far too much time just trying to format it right, or you find it crashes when you try to open a 200 page document with tonnes of figures. It just wasn't worth it.

I moved to LaTeX for typing my thesis, and after a few days learning how to use it was hooked. Despite being a lot longer than my Honours dissertation (which I made in Word), my thesis has been far easier to typeset.

Then I moved to R for statistics, despite the institutions I was working with offering SAS and GenStat but no R courses, simply because I could install it on my own computer. Eventually I learnt to use R for all my graphs, because it was actually easier than using a spreadsheet (once you got the hang of it) and made nicer results. This was daunting at first, but well worth the time invested.

I too am no statistics expert. But I was able to get assistance from the university to work out what analytical methods would be appropriate for my data, and then learnt how to do that in R. I taught myself how to make graphs in R from online resources and the book "R Graphics" by Paul Murrell, which I bought - a good book, but you still find yourself using the internet a lot too.

Finally I moved to Linux as well...

Start out right, and don't muck around with software that really isn't ideal. You'll either move to LaTeX and other similar software eventually anyway and wish you had done so earlier, or regret it when you have to spend hours and hours just formatting your thesis at the end. 

After the nightmare it was formatting a 67 page Honours dissertation in Word, I shudder to think how much I'd be fussing round with my 260+ page thesis if I was doing it in Word or OpenOffice.

I'd recommend you invest the time learning LaTeX for your thesis - its far easier than it looks and you'll never regret it. 

For graphs and stats you may find it best to use whatever software your university can provide tuition for, but if you're willing to take the dive into R, once again you'll never regret it.

I've learnt this the hard way - I hope you can learn it the easy way! Best wishes with the PhD!

---

