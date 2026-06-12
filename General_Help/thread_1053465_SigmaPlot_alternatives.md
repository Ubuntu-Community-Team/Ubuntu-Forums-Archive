---
title: "SigmaPlot alternatives?"
date: 2009-01-28
forum: General Help
---

### Post by deep888 on 2009-01-28
Are there any Linux clones/alternates for the plotting and graphing software SigmaPlot? Preferably free? 
I'm not exactly a Ubuntu veteran, so installation tips would also be welcome.
Thanks
Deep

---

### Post by frogotronic on 2009-01-28
gtk plot

try :  [http://sal.jyu.fi/index.shtml](http://sal.jyu.fi/index.shtml)

scigraphica

---

### Post by Wayne_V on 2009-01-28
Not familiar with SigmaPlot, but if you like Matlab check out Scilab.   Or, people rave about R ([www.r-project.org](www.r-project.org)).  Both are available via apt:

$ apt-cache search scilab
$ apt-cache search "^r-base"

---

### Post by deep888 on 2009-01-30
yeah thanks. r seemed to hardcore for me right now, maybe later, when I'm actually a statistician or something. QtiPlot is working fine for me now.

---

### Post by pseudotheist on 2009-01-30
Heh, my wie just told me yesterday she needs SigmaPlot.  Will either or both QtiPlot or GTKPlot work compatably with SigmaPlot files, transferring back and forth?  Is one of them more robust or more similar to SigmaPlot?

I know nothing of SigmaPlot, so any advice would be greatly appreciated.

---

### Post by Catalyst2Death on 2009-01-30
There's R which isn't very hard to use, its a little hairy at first, but it doesn't take much to get meaningful results.  It handles small amounts of data fairly nicely.  There's also ROOT: [http://root.cern.ch/](http://root.cern.ch/) which is used by high energy physicists to do their work.  ROOT includes RooFit which is a fitting framework.  It is also C++ based, so if you know C++ getting ROOT to do what you want is almost trivial, although it would take more work to get a plot out of ROOT than R (I think).

I would hazard to say that R and ROOT would do most of what SigmaPlot can do and more, but it might not be as user-friendly.  R is available in the repositories, as is ROOT, but the ROOT packages are notoriously out of date (IMHO)  Instructions for installing ROOT:
[http://ubuntuforums.org/showthread.php?t=1043769](http://ubuntuforums.org/showthread.php?t=1043769)

R: [http://www.r-project.org/](http://www.r-project.org/)

I have a good introduction to R laying around somewhere if your interested.  I just don't have the link handy, but I could dig up the PDF easily enough.

---

