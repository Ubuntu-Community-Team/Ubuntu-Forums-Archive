---
title: "Scientific Ubuntu: &quot;Subuntu&quot;"
date: 2007-05-31
forum: Education &amp; Science
---

### Post by sersetto on 2007-05-31
I would like to know the opinion of other scientists and/or educators on the following idea.

I think there should be a Scientific Ubuntu Team along with the 
others ([https://wiki.ubuntu.com/Teams](https://wiki.ubuntu.com/Teams)). One thing I would like 
the Scientific team to do is to develop "free" software to compete and liberate 
us from the "slavery" of proprietary scientific software and their huge fees.
For example one thing I think would be neat is to have scientific commands
from terminal: a sort on scientific Linux where in addition to normal Linux command you have now scientific commands. Let say I want to know the auto correlation of my data I just type from terminal "autoc mydata > automydata" and my auto correlation function is saved in the file "automydata" or even better "autoc -p mydata" and the auto correlation is plotted on the screen and so on... 

I know that many of this things can be done using "free" software out there, but 
still like the idea of having everything integrated and in just one command line without 
starting a different program. This will be useful when your write shell script 
to do analysis of several files.

I think this can be a way also of making more appealing ubuntu-Linux in an 
university environment.

Well, these were my 2 cents. 
Thank you very much for your suggestions,ideas,criticism,.... 
Happy ubuntu to everybody. :)

---

### Post by spin2cool on 2007-05-31
There's already a group who maintains an installation script for scientific software:
[http://scibuntu.sourceforge.net/](http://scibuntu.sourceforge.net/)

Talk to them if you're going to be starting anything up.

---

### Post by xadder on 2007-06-01
I don't see how this one-command idea would work. Science usually comes with a thousand complications.
To take your example, 

"autoc mydata > automydata" and my auto correlation function is saved in the file "automydata" or even better "autoc -p mydata" and the auto correlation is plotted on the screen and so on..
 
I would want to know if the data file had missing or invalid values (often NaN, -999, ..... take you pick). Would it have header records to explain the data. Comma or space seprated, one or more columns, etc.?
When you plot, would you want linear or log or semi-log axes, times-roman labels, or LaTeX symbols? 

Ubuntu + python/perl/ruby/awk//your-favourite-script  + pylab/octave/kplot/your_fgavourite_plotter can cope with all of  this very well. I don't see how this could be condensed into one-liners.

---

### Post by raja on 2007-06-02
I agree that python + Scipy + matplotlib, or perhaps Octave is the best solution for this.

---

### Post by NikoC on 2007-06-02
I personally would not download a Scientific Ubuntu already packed with apps... I prefer to do a clean install and add programs on the go as I see need to use them.
But perhaps you are right that a S.U. might bring more people to 'the other side'.

---

### Post by xadder on 2007-06-03
Better to use the energy to improve the scientific progs in my opinion. (See recent discussions on chemical drawing packages for example).  Or, and I hate to say, improve the exhcangability of files with MS stuff.  Most people  I know are nervous of Linux because they can't exchange documents with Word/Excel users. OO still struggles here.

Also, even looking at the scibuntu link above it is easy to see where users will have different preferences. Eg. I prefer now to use texlive, whereas scibuntu had tetex. They didn't have matplotlib/pylab, etc.  This is't a big problem as basic Ubuntu lets you use all of these very easily.  That's what great about Ubuntu! (Or Debian or Linux in general)

---

### Post by zenkaon on 2007-06-07
Have you had a look at 
[https://www.scientificlinux.org/](https://www.scientificlinux.org/)

It's essentially Red Hat Enterprise Linux but it has been recompiled (re-branded) by the good people at Fermilab and CERN. It is installed on virtually every computer on the GRID and is great at doing scientific stuff. Not nearly as nice as (k)ubuntu for the desktop though, it's the disto I left for kubuntu mainly due to hardware support for my laptop.

If you would like an analysis package, then you could check out
[http://root.cern.ch](http://root.cern.ch)

It's mainly used as a particle physics tool but the data analysis you can do with it is fantastic. Hundreds of scientific functions,routines and classes. It even provides a framework for you to do multi-threading computing scalable to (I think) around 256 CPU's. Plus its released under the good old GNU GPL.

---

### Post by tkjacobsen on 2007-06-09
[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

Check it out -- and help make it better.

---

### Post by WebDrake on 2007-06-10
> **sersetto said:**
> 
I think there should be a Scientific Ubuntu Team along with the 
others ([https://wiki.ubuntu.com/Teams](https://wiki.ubuntu.com/Teams)). One thing I would like 
the Scientific team to do is to develop "free" software to compete and liberate 
us from the "slavery" of proprietary scientific software and their huge fees.


There are very good reasons why wider free software adoption is desirable in science, relating not just to fees but also to good scientific practice---we need our tools to be open to scrutiny.

You raise a number of issues so it's probably worth dealing with them separately on their own terms.  Let's start with the simplest first, your command-line utilities proposal.  Since functions like these are easily available in any data analysis environment, it might be kind of redundant.  I can see the attraction of having a few simple utilities to hand, like the autocorrelation function you describe, but nothing more complicated.

There's a reason why people use separate environments for data analysis---different kinds of task require distinct syntax.  The UNIX shell was designed for system manipulation and is not friendly to mathematical operations.  In addition system shell syntax changes from platform to platform, whereas a dedicated environment can generally be used without reference to the system underneath.  For this reason I don't see your proposal as being workable beyond *very* basic stuff---it would be too cumbersome---though if you're keen, I'd encourage you to go ahead and work on it.

Now to the more general issues raised.  I think we can divide this into two parts---on the one hand, the development and encouragement of free software tools for scientific work, and on the other hand the development of Linux distributions (or Ubuntu flavours) dedicated to scientists.  The two have some distinct aspects which are worth discussing.


[size="4"]**Scientific free software**[/size]

As shown at the link provided by tkjakobsen, there are a lot of free software projects out there, covering a whole range of applications.  Some of these---e.g. R---are already world leaders in their particular field and indeed some have no effective proprietary competitors.  Others lag behind.  In pushing free software there are four key problems we need to deal with:

[list=1]
[*]**Software functionality and user-friendliness.**  This is the "obvious" problem---there are many cases where the proprietary product provides greater functionality and ease of use than any free software solution.  Microsoft Office and MATLAB both spring to mind (I'm sure others can provide further examples).  Since scientists' business is not software freedom but results, they will seize any tool that can give them an edge.

[*]**Cross-platform implementation of free software solutions.**  We can't be myopic about this and assume that pushing free software involves converting everyone to Linux.  Some people may be restricted to Windows because there are tools they need for which there is no free equivalent.  Rather than creating an "all or nothing" situation we need to make it possible for them to use free software *as much as possible* without getting in the way of their essential needs.

[*]**Lock-in to existing packages.**  Certain proprietary packages have become de facto standards---again, MS Office and MATLAB spring to mind.  "Lock-in" here is more complicated than mere compatibility issues---in fact data and code can often be transferred easily.  The real causes tend to be social, involving a preference for recognisable brands and "reliable" names.  One of the reasons for Ubuntu's success is that it has so clearly established both an identity and a clear picture of who the buck stops with, as well as a reliable and predictable release pattern.

[*]**Technical support, training and certification.**  Although the community is almost invariably very helpful many organisations (academic and others) will want some form of accountability and guaranteed support for their tools.  The charitable responses given on mailing lists and forums are too uncertain where money and careers are at stake.  The comments above about identity, buck-stopping and reliability apply here even more strongly.
[/list]


[size="4"]**Science-dedicated distros and Scientific Ubuntu**[/size]

The distro side of things is somewhat different and in some cases even contradictory to the software development side.  For example, one thing important to the success of a science-oriented distro is the easy availability of key proprietary tools such as MATLAB, Mathematica and so on.  As above with the question of cross-platform implementations, we need to be open-minded to the fact that some people cannot work effectively without certain essential tools, some of which are non-free.  It's rather analogous to the situation with media codecs---we don't like it, but it should be possible for those who can't do without it.

What is needed in different scientific situations varies widely and the case of Scientific Linux is instructive---a very stable and consistent base (a slightly-modified RHEL) customised to allow for site-by-site flexibility on key areas.  This should be an inspiration for any Ubuntu-based effort.

Looking at Scibuntu as it exists now I think they are going about things in somewhat the wrong way.  An install script is a rather clumsy mechanism compared to what could be done.  Ubuntu Studio have really done very nice work in this regard, creating an Ubuntu "derivative" which is not actually a separate distro but a collection of compatible packages which can be installed either fresh or from repositories as an addition to "vanilla Ubuntu".

I would suggest the Scibuntu project could go along similar lines, with members working to tested and up-to-date versions of key scientific packages.  Some of this could probably be done within the main Ubuntu project, with an independent "scibuntu" repository for further material, special needs and so on.  Following the example of Scientific Linux we could have some separate "metapackages" for different needs---scibuntu-hep, scibuntu-biochem, scibuntu-psych, scibuntu-math, scibuntu-stats, ...---along with a set of policies guiding others to provide their own compatible custom packages or setups.

We could provide a "scibuntu" install CD as a courtesy for those who want it, or to test it on a LiveCD, but as per NikoC's requirements there would be no *need* for a separate distro.  What would be needed is a regular, predictable release of the Scibuntu packages in sync with the main Ubuntu release.

I would be interested to know what people from the Scibuntu project (and others) think of these ideas ....

---

### Post by Fingolfin on 2007-10-05
WD, I agree that a separate distribution (Scibuntu) would certainly put additional burden on the Ubuntu developers/maintaners.
Yet. something needs to be done in light of many users reportedly having trouble when installing key scientific applications.

We have this great Linux called Ubuntu, and there is software like OpenFoam, Calculix, Salome,, to many to name them here,.... on which hundreds of hours are wasted by Ubuntu users just to make them work (if possible at all since by Murphy's law they always work on somebody else's computer as the one who attempts to install it is always missing some *.lib or other obscure file). 
In the case of MS Win XP, the applications (not just scientific but any application) just WORK at first from "setup.exe" without all that wrestling with the spurious error/config messages.

I would welcome the idea of simply having the most wanted scientific applications available from repositories like Universe/Multiverse/... Scienceverse???  from where the users can install them in much the same manner as they download and install everything else.

---

### Post by euler_fan on 2007-10-07
> **Fingolfin said:**
> WD, I agree that a separate distribution (Scibuntu) would certainly put additional burden on already stretched pool of Ubuntu developers/maintaners.
Yet. something needs to be done in light of many users reportedly having trouble when installing key scientific application.

We have this great Linux called Ubuntu, and there is software like OpenFoam, Calculix, Salome,, to many to name them here,.... on which hundreds of hours are wasted by Ubuntu users just to make them work (if possible at all since by Murphy's law they always work on somebody else's computer as the one who attempts to install it is always missing some *.lib or other obscure file). 
In the case of MS Win XP, these wonderful and useful applications just WORK at first from "setup.exe" without all that wrestling with the spurious error/config messages.

I would welcome the idea of simply having the most wanted scientific applications available from repositories like Universe/Multiverse/... Scienceverse???  from where the users can install them in much the same manner as they download and install everything else.

+1

I agree the problem is mostly packaging the software for Ubuntu much more than the lack of a particular distro "optimized" for scientific computing. Besides, most people have a few tools which they prefer to use, know them, and can be shown where to get them.

---

### Post by rybu on 2007-10-08
I understand how some people might desire a "scibuntu distro," but you have to ask, who exactly would it be for?  Things like this only really come to life if the people who need the software take ownership of the process of integrating it into a distro. 

In my field (mathematics), almost all the software people use is already open-source.  Much of the software I use is already in the Ubuntu repository, and the stuff that isn't is mostly open-source, but too sloppy for general distribution.    Those "sloppy" packages, people just don't have the time to patch up, and for most non-experts, the process of mending the packages together into a distro would be well past the amount of time and effort they'd be willing to put in to the process.

Most people deal with pretty specialized tools for rather specialized problems, and rarely develop apps suitable for general usage.  The general tools we use are things like: GNU C++, Python, LaTex, GAP, the standard C++ libraries, etc.   There are a few rare examples of more "niche" tools that make it into the Ubuntu repository, but they're few and far between. 

I could see maybe sometime in the future when this would be a more reasonable proposition -- once open-source scientific computing has matured a little more.  But IMO the impetus has to come from the developers of the bits.

---

### Post by Fingolfin on 2007-10-09
With the new .package system there is even a chance that *.deb and *.rpm formats  will become obsolete in the future. 
The racing game VDrift [http://vdrift.net/](http://vdrift.net/) is a nice example of how a complex program can be installed easily on any distribution from a single package. The very same thing could be done with scientific applications at least in *.deb format :-)

---

