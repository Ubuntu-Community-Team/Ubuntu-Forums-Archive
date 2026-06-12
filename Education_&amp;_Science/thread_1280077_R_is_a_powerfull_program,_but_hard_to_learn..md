---
title: "R is a powerfull program, but hard to learn."
date: 2009-10-01
forum: Education &amp; Science
---

### Post by awayguy on 2009-10-01
halo

i use R since maybe a week now, as far i've seen its a very powerfull program.

the damn thing is, its hard to learn, and there are nowhere really usefull scripts which could help. there is nowhere something which would intruduce the main and important operations of R step by step. sure there is this big Help document but it always starts somewhere, where a newbie has no idea.

maybe i'm wrong, but i searched a lot how to plot and how to adjust the scale of the graph but i couldnt find stuff nowhere.

i think R has potential and there would be a lot of more people who would use it, but as they start working with R, they get really fast in trouble.
i'm sure many gave allready up on this.

correct me if i'm wrong, and if you find something usefull, post it here

with regards

---

### Post by gunksta on 2009-10-01
howdy awayguy. I think I responded to another thread you threw up here.

I attached a total of three zip files. Read the two in the "basics" attachment first. The R Inferno is immensely entertaining and is meant to be a parody of Dante's Inferno, but it teaches you the nuances of the language. If English is not a language you are strong in, this one might be a bit much (which is funny since the original is not in English).

The other two are dry as dirt, but are very accessible, provided you have at least a basic understanding of programming.

The most important concept in R is the idea of vectorization. Because R is an interpreted languge, loops are rather slow. Avoid them whenever possible (or accept the speed penalty). The stuff I have attached will beat this idea home better than I can.

I would write more, but I need to go upgrade my computer to Karmic and see if it crashes.  :guitar:

---

### Post by IanH on 2009-10-01
[http://zoonek2.free.fr/UNIX/48_R/all.html](http://zoonek2.free.fr/UNIX/48_R/all.html) is one of the better introductions I've found. Also, rseek.org makes it much easier to find information on specific tasks.

For plotting, that will depend on what type of plot you want. plot() is the basic function, and will usually give you something sensible. Most plot functions take ylim and xlim parameters, should give you your scaling.

---

### Post by earlycj5 on 2009-10-01
stackoverflow has a growing R community as well for questions:


[http://stackoverflow.com/questions/tagged/r](http://stackoverflow.com/questions/tagged/r)

---

### Post by gunksta on 2009-10-01
I almost forgot to mention this site:

[http://www.statmethods.net/]("http://www.statmethods.net/")

It is meant for people moving from SPSS to R, but I think it could be useful to anyone learning R. I think it's pretty well organized.

(My computer told me it would take over 4 hours to download the updates so I came back.)

---

### Post by machoo02 on 2009-10-02
And don't forget about [RSeek]("http://www.rseek.org/") for searching about R specific topics.  I've also attached a couple of reference cards and one R tutorial .pdf.  I have several others, such as Verzani's 'Simple R', but they're a little to big to attach here, so PM me if you want a copy.  There's plenty of good documentation out there for R, it just takes a while to find it and begin learning how to use it.

---

### Post by akniss on 2009-10-03
I'm quite surprised nobody has posted this yet:

[http://cran.r-project.org/doc/manuals/R-intro.pdf](http://cran.r-project.org/doc/manuals/R-intro.pdf)

It is the most well-known and most-recommended introduction to R in the R mailing lists. I have a print copy that I lend out to all my students while they're learning the basics.

---

### Post by ahmatti on 2009-10-04
> **awayguy said:**
> halo
maybe i'm wrong, but i searched a lot how to plot and how to adjust the scale of the graph but i couldnt find stuff nowhere.


You definitely need to learn how to search! R has so many good introductory treatments out there, that I can't believe that you couldn't find anything if you used any sensible search terms!

Anyway, here is one more link to contributed R documentation [http://cran.r-project.org/other-docs.html](http://cran.r-project.org/other-docs.html). Which can be easily find by clicking the manuals link under the R main page [www.r-project.org](www.r-project.org)!

If you can't find what you need from the links in this thread I suggest you buy yourself a decent R book. "Introductory statistics with R" seems to be recommended often enough [http://staff.pubhealth.ku.dk/~pd/ISwR.html](http://staff.pubhealth.ku.dk/~pd/ISwR.html).

---

### Post by memilanuk on 2009-11-23
Yeah the thread is a little dated, but it comes up in searches so I thought I'd throw this one out there too:

[http://www.r-tutor.com/](http://www.r-tutor.com/)

It's slowly growing, good content, nice clean design.  I'm not sure it's ready (yet) to replace 'Introductory Statistics with R' (Dalgaard) or 'Using R for Introductory Statistics' (Verzani), but it is online, and free.

---

### Post by aaronchall on 2009-11-30
Stats are that 3 in 4 pirates prefer R...rrrrrrr...

---

### Post by earlycj5 on 2009-11-30
.

---

### Post by StephenWoods69 on 2010-01-07
> **memilanuk said:**
> Yeah the thread is a little dated, but it comes up in searches so I thought I'd throw this one out there too:

[http://www.r-tutor.com/](http://www.r-tutor.com/)

It's slowly growing, good content, nice clean design.  I'm not sure it's ready (yet) to replace 'Introductory Statistics with R' (Dalgaard) or 'Using R for Introductory Statistics' (Verzani), but it is online, and free.


Thanks for this link the site is definitely good as I was tinkering away with barplot almost immediately.
In regard to the GUI argument I've used GUI's all my computer life but find the console really easy with R but maybe that's because I haven't moved unto the really advanced stuff yet.

---

### Post by hubie on 2010-01-07
> **StephenWoods69 said:**
> 
In regard to the GUI argument I've used GUI's all my computer life but find the console really easy with R but maybe that's because I haven't moved unto the really advanced stuff yet.

In my experience, GUIs are a hindrance when you get to the really advanced stuff.  They are nice when you can open a file with a couple of mouse clicks instead of typing in a string of characters, but even if they are equipped to handle the advanced stuff, you usually need to repeatedly click down multiple layers to do what you want.

---

### Post by earlycj5 on 2010-01-07
> **hubie said:**
> In my experience, GUIs are a hindrance when you get to the really advanced stuff.  They are nice when you can open a file with a couple of mouse clicks instead of typing in a string of characters, but even if they are equipped to handle the advanced stuff, you usually need to repeatedly click down multiple layers to do what you want.

When I was finishing my dissertation last month I found myself working with ArcMap, yuck!  I digress.  I did actually find myself thinking, "I wish that I could just type this out rather than point and click, it would be so much faster if I could do this with R."

Yes, there are ways to do what I was doing with ArcInfo, but I'm not as skilled with that as R.

Point is, I agree wholeheartedly.

---

### Post by gunksta on 2010-01-07
> In my experience, GUIs are a hindrance when you get to the really advanced stuff. They are nice when you can open a file with a couple of mouse clicks instead of typing in a string of characters, but even if they are equipped to handle the advanced stuff, you usually need to repeatedly click down multiple layers to do what you want.

I'm not sure this has to be the case. Lately I have been using R via Vim (vimrplugin2) and Rkward. Both have their advantages. While the learning curve for Vim is higher, it's extraordinarily versatile and it handles remote connections (to R) without a whimper (with a little trickery on my part).

But I really really like the way Rkward handles things when I hit ?foo. Each help request gets it's own tab in the UI, without blocking up the R Console (it uses R's HTML help output). When I'm using Vim, I sometimes use this same output and throw everything in FireFox, but I have too many tabs open here as it is. The last thing I need is three more to help me remember various magical incantations. Besides, FireFox stays on Desktop 1, while R is usually running on Desktop 2 or 3, meaning I have to change desktops to read the help. Rkward's handling on R's help system is really really nice. 

Moreover, it provides a nice, spread-sheet like way to VISUALIZE my dataframes (if desired) but makes it easy for me to reach down and grab a hold of the console directly if that's what I want.

Rkward needs to continue maturing and I'll be the first to admit that I don't take full advantage of it's menu options, but I really do like certain aspects of using R within Rkward. Cantor will be released with the next version of KDE and I'm curious to see how it stacks up against Rkward. For myself, I will keep my Vim setup installed and take advantage of either Rkward or Cantor (probably not both) when these tools seems better to me.

As Kate's vi emulation improves, I think we can expect to see these improvements passed on to programs like these, which could really start to blur the lines (and doubtlessly harden people's attitude's toward their pre-selected opinions).

---

### Post by samden on 2010-01-07
I agree Gunksta that there are some advantages to GUIs - but note that all the advantages you mention about RKward are basically different ways of displaying the output of your console input. You're still finding the most efficient way of getting help to be typing ?foo for example, rather than trawling through menus.

GUIs can be great at displaying output, but I'd have to agree with hubie that the console is generally the best way of entering input - although every rule has its exceptions.

RKward does create a good balance between console input and GUI output, giving the best of both worlds, although I find I still stick to a plain text editor and console the majority of the time (Gedit on Ubuntu, Notepad++ on Windows).

---

### Post by gunksta on 2010-01-07
> **samden said:**
> You're still finding the most efficient way of getting help to be typing ?foo for example, rather than trawling through menus.

Good point.

---

### Post by euler_fan on 2010-01-07
I like Emacs (+) ESS for handling R (no VIM vs EMACS war intended . . . I used to use Cream and really liked it).

Perhaps the correct paradigm for learning R is to treat it as a language with a very robust set of libraries built in.

---

### Post by StephenWoods69 on 2010-01-08
Just found this site which lets you use raw data and I thought I'd include it for those who need some data for use with R
Enjoy
[http://lib.stat.cmu.edu/datasets/](http://lib.stat.cmu.edu/datasets/)

---

### Post by hubie on 2010-01-08
> **StephenWoods69 said:**
> Just found this site which lets you use raw data and I thought I'd include it for those who need some data for use with R
Enjoy
[http://lib.stat.cmu.edu/datasets/](http://lib.stat.cmu.edu/datasets/)

Thank you for that link.  There are some very interesting data sets there (*e.g.*, the shooting stats for Vinnie Johnson of the Detroit Pistons from 1985 through 1989).  The page has obviously been around for a long time, but it was one I was not previously aware.  

A great way to learn R is by playing around with data.  Usually I start out with the meticulous records of the gasoline purchases and tracked mileage for the various automobiles I have owned, so it is nice to have a repository of new data.

---

### Post by StephenWoods69 on 2010-01-08
Just looking around again and saw this [http://addictedtor.free.fr/graphiques/.]("http://addictedtor.free.fr/graphiques/")
It's pretty cool showing not only the graphs but the code for how they made them.
Might help with some of the shooting stats.
I used to keep records of my cars mpg but it became too depressing so I gave up (sigh) besides I was on Windows then and didn't even know about R.

---

