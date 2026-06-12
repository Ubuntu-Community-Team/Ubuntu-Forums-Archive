---
title: "labplot or qtiplot"
date: 2007-07-20
forum: Education &amp; Science
---

### Post by unixguru on 2007-07-20
I think Labplot is no longer being developed and qtiplot is actively developed but not in the repos and if I am correct they conflict. I have not used any windows software(origin in particular), so I don't care what features of origin these two have, I just want to plot 2d and 3d functions, do some basic stuff like interpolation, data fiting etc. So which of these is easier for my purposes. It is also important for me  that the plots look good.

---

### Post by raja on 2007-07-21
I have been using qtiplot and it is pretty good. Also look at rlplot which is in the repos.

---

### Post by tgalati4 on 2007-07-21
There is always gnuplot.  An old but stable program.

---

### Post by unixguru on 2007-07-21
> **tgalati4 said:**
> There is always gnuplot.  An old but stable program.

Ease of use is my first priority and can gnuplot do interpolation and curve fitting?

---

### Post by curley_sue on 2007-07-31
> **unixguru said:**
> I think Labplot is no longer being developed and qtiplot is actively developed but not in the repos and if I am correct they conflict..

in order to install qtiplot from the repos:

deb [http://195.198.146.229/debian/](http://195.198.146.229/debian/) i386/
deb-src [http://195.198.146.229/debian/](http://195.198.146.229/debian/) source/
deb [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons) sarge /
deb-src [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons) sarge /


personally i like best  (it's all in the repos):
python+ipython+matplotlib+scipy

(run it using: ipython -pylab )

matplotlib has similar syntax to matlab but python allows you a much more fast, flexible and robust environment.

for some examples:
[http://www.scipy.org/Cookbook/FittingData](http://www.scipy.org/Cookbook/FittingData)
[http://matplotlib.sourceforge.net/tutorial.html](http://matplotlib.sourceforge.net/tutorial.html)

another advantage is that installing the enthought python package on a windows machine ( [http://code.enthought.com/enthon/](http://code.enthought.com/enthon/) ) let's you have compatible environment on windows (in case you have to work on different computers where you have only M$ Win).

Last but not least: python is good to know also for many other things (other than data analysis) - enjoy!

---

### Post by Castar on 2007-08-03
What makes you say that Labplot is not developed? There is a 1.6.0 pre3 prerelease version out on May 2007. I wouldn't write off Labplot easily. Qtiplot is nice. 

Gnuplot, on the other hand is not targeting the people that Qtiplot & Labplot are as they are mainly Origin clones. I'm not saying that it is not good, but it doesn't have a native GUI as the other two programs do.

---

### Post by mrsurf on 2007-09-06
Can u tell where should I put these lines or should I download from these or it will install from Installer after putting these linessss???
How AND WHICH FILE HOULD i PUT THESE LINES???
:confused:
> **curley_sue said:**
> in order to install qtiplot from the repos:

deb [http://195.198.146.229/debian/](http://195.198.146.229/debian/) i386/
deb-src [http://195.198.146.229/debian/](http://195.198.146.229/debian/) source/
deb [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons) sarge /
deb-src [http://debian.physik.hu-berlin.de/addons](http://debian.physik.hu-berlin.de/addons) sarge /


personally i like best  (it's all in the repos):
python+ipython+matplotlib+scipy

(run it using: ipython -pylab )

matplotlib has similar syntax to matlab but python allows you a much more fast, flexible and robust environment.

for some examples:
[http://www.scipy.org/Cookbook/FittingData](http://www.scipy.org/Cookbook/FittingData)
[http://matplotlib.sourceforge.net/tutorial.html](http://matplotlib.sourceforge.net/tutorial.html)

another advantage is that installing the enthought python package on a windows machine ( [http://code.enthought.com/enthon/](http://code.enthought.com/enthon/) ) let's you have compatible environment on windows (in case you have to work on different computers where you have only M$ Win).

Last but not least: python is good to know also for many other things (other than data analysis) - enjoy!

---

### Post by Castar on 2007-09-06
Which K/Ubuntu are you using?

---

### Post by raja on 2007-09-06
> **mrsurf said:**
> Can u tell where should I put these lines or should I download from these or it will install from Installer after putting these linessss???
How AND WHICH FILE HOULD i PUT THESE LINES???
:confused:

Depends,  of course, on what you want to install. It may be better that you use Linux for some time and get familiar with repositories and such before adding other sources. 
You can read the wiki [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") for relevant information.

---

