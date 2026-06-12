---
title: "OCTAVE 3.0.0 &amp; GUI frontend"
date: 2008-01-10
forum: Education &amp; Science
---

### Post by thisismalhotra on 2008-01-10
Hey Guys :popcorn:

For all those octave users who are looking for a decent GUI front end, Qtoctave is a very nice solution. A new version for the same 0.7.1 just came out and I have been using that for a while, seems to be stable and very good, gives just like MATLAB IDE. 

Here is the link to website

[http://qtoctave.wordpress.com/what-is-qtoctave/](http://qtoctave.wordpress.com/what-is-qtoctave/)

to download: -

[https://forja.rediris.es/frs/?group_id=60&release_id=298](https://forja.rediris.es/frs/?group_id=60&release_id=298)

For those ubuntu/debian based linux users who dont like to build from source or dont want to go through the trouble can buzz me, I have a .deb for it (dont have a website to upload it so will e-mail)

FYI, I have a .deb for new octave 3.0.0 too in case somebody needs it. Octave 3.0** ROCKS !!**

*Happy number crunching*

---

### Post by slimdog360 on 2008-01-12
qt, nuff said. looks good though.

---

### Post by propensity on 2008-01-13
did you get easy_plot to work? I get some QSocketNotifier error when i try to plot using easy_plot.:confused:

---

### Post by thisismalhotra on 2008-01-14
Hey propensity,

I never tried easy plot cause, I like jhandles personally. I can try using it and give you a feed back in couple of days.

Just out of curiosity, are there any advantages to use easy plot:confused:

---

### Post by ginobvhc on 2008-01-14
i got some problems to can easy plot work some body can do that???
and some one got oct 3.0.0 deb pack ???

---

### Post by thisismalhotra on 2008-01-14
I have oct 3.0.0 deb .. how should I send that to you !! Still working on easy plot, but I prefer jhandles

---

### Post by eiffleduarte on 2008-01-15
I would love to get this deb of octave 3.0. Did you build it including octave-forge?
I guess that other users would also want to install octave 3.0. Is there a way I could download this package?

Thanks!

---

### Post by thisismalhotra on 2008-01-15
I am not sure if I have octave-forge in it .. but I will double check and let you  know, as far as I know I dont, but you can build octave forge very easily from octave menu.
Send me yur emai ID and I will send you the .deb packages.

---

### Post by s57nev on 2008-01-17
One question. Octave works great there is only one problem. Plots doesn't have zoom option like Matlab. I work with very long vectors and have huge problems setting plot limits in Octave. GNU plot just isn't enough for my needs any more. Is there alternative for plotting ? With save as image option ?

---

### Post by thisismalhotra on 2008-01-17
I personally like jhandles ... it can rotate it in 3d and zoom too, but you might wanna try easyplot too. Heard a lot about it but could not get it to work till now .. will update once working

---

### Post by thisismalhotra on 2008-01-17
Update Qtoctave team has loade the .deb file onto this link... so you guys can download it form here too..

[http://www.mediafire.com/?21jqdnetymn](http://www.mediafire.com/?21jqdnetymn)

GM

---

### Post by thisismalhotra on 2008-01-23
:popcorn::KS

UPDATE FOR ALL USERS TRYING TO FIND ALTERNATE TO Gnuplot OR TRYING TO MAKE EasyPlot TO WORK IN QTOCTAVE..

Qtoctave team just came up with new version of Easy Plot => EasyPlot 1.1. Can download source from here: -

[https://forja.rediris.es/frs/?group_id=60&release_id=299](https://forja.rediris.es/frs/?group_id=60&release_id=299)

I have installed it, works fine with qtoctave 0.7.1 and does not give the QSocket notifier error.

Octave ROCKS!!:guitar:

P.S: As ususal I have the .deb package, PM me incase you need one!!

---

### Post by uday_adusumilli on 2008-02-02
Hi.. 

i am pretty new to octave and i am trying to install jhandles package. But I am getting an error:

error: the following dependencies where unsatisfied:
   jhandles needs java >= 0.0.0

I have java installed on my machine. Can you please tell me where I am going wrong.

Thanks in advance.

---

### Post by thisismalhotra on 2008-02-04
Hey uday,

If I remember right you will need JRE (Java rintume environment) and JOGL (Java OpenGL -  I think it comes with JDK) before installing jhandles. Also, there is a java package in octave-forge too, I think you will need that too.

Basically you will need to fulfill all the dependencies...

See this links for the dependencies

[http://octave.sourceforge.net/java/index.html](http://octave.sourceforge.net/java/index.html)

[http://octave.sourceforge.net/jhandles/index.html](http://octave.sourceforge.net/jhandles/index.html)

TC

GM

Also here is a deb for easyplot, another plot package I found good. Now I can say it is better than jhandles....

---

### Post by Tantor on 2008-03-14
Hi people,

following the various threads I have set up octave 3.0 + qtoctave (thanks thisismalhotra!) and everythings seems to be going just fine. Does someone know how to ...

(1) Change the fonts in qtoctave? I have a large resolution and my life would be easier if I could enlarge a bit the fonts!

(2) Stop something before its completed? Ctrl+C doesn't work (it does work in the terminal interpreter). For example, if I forget a ";" in a long variable I would like to stop qtoctave when it's showing its content.

Thanks in advance!

---

### Post by thisismalhotra on 2008-03-15
Well about your 2nd problem .. if you are using Qtoctave there is an x button n top in menu which will stop your process...

ABout the fonts try and look around in the config menu and see if there is an option....??

HTH

---

### Post by Tantor on 2008-03-15
Thanks. I hadn't seen that big X button! jaja. Using qtoctave config I can change the editor and terminal fonts, but I don't know how to change the fonts on the menues, buttons, etc. It's not THAT important but it would make my life easier.

My guess is that there is some external configuration for qt apps. For kde apps I change this kind of settings using kcontrol. Maybe there is something equivalent for qt apps.

---

### Post by dave373 on 2008-03-25
I am trying to install qtoctave onto gutsy and am having no luck. 
I am getting an error with configure as it needs qmake  (which I assume is part of libqt4-dev after an apt-cache search) 
libqt4-dev depends on libpq-dev which appears to have a package error
 .. Any hints?

---

### Post by thisismalhotra on 2008-03-27
> **dave373 said:**
> I am trying to install qtoctave onto gutsy and am having no luck. 
I am getting an error with configure as it needs qmake  (which I assume is part of libqt4-dev after an apt-cache search) 
libqt4-dev depends on libpq-dev which appears to have a package error
 .. Any hints?

Please install following libs from synaptic and run the configure command again..

libqt4-core
libqt4-gui
libqt4-qt3support

This thread might help

[http://ubuntuforums.org/showthread.php?t=707854](http://ubuntuforums.org/showthread.php?t=707854)

---

### Post by TheDro on 2008-05-05
Do we have to install gnuplot to be able to use plot(x,y) in QToctave (or just octave since I get the same error message) and if so, do we have to download it separately on the internet because I can't find it on add/remove applications.

Thx in advance, TDro

---

### Post by thisismalhotra on 2008-05-06
> **TheDro said:**
> Do we have to install gnuplot to be able to use plot(x,y) in QToctave (or just octave since I get the same error message) and if so, do we have to download it separately on the internet because I can't find it on add/remove applications.

Thx in advance, TDro

Yes GNUPLOT need a separate installation.... Alternatively you can install easy_plot too.
Anyways open synaptic and search for gnuplot and install it from there.

---

### Post by BennBuntu on 2008-05-07
Any hints on configuring qtoctave to use easy_plot for plotting?
Says to reconfigure but can't find much in the docs.
Both are latest version built from source.

---

### Post by thisismalhotra on 2008-05-07
> **BennBuntu said:**
> Any hints on configuring qtoctave to use easy_plot for plotting?
Says to reconfigure but can't find much in the docs.
Both are latest version built from source.
It's really easy...

Config -> General Configuration -> Octave -> Check use easy plot -> browse to paths (/usr/bin in linux usually) -> ok 

restart qtoctave

---

### Post by BennBuntu on 2008-05-07
Almost too easy, ](*,)
default was /usr/local/bin/easy_plot

Cheers

---

### Post by thisismalhotra on 2008-05-08
> **BennBuntu said:**
> Almost too easy, ](*,)
default was /usr/local/bin/easy_plot

Cheers

:lolflag:

---

### Post by mattycoze on 2009-02-12
Is there a new Octave frontend for the 3.0.1 version that is currently on the Ubuntu Repositories?
I've installed 3.0.1 and the QTOctave frontend doesn't seem to be working; I get the following error:
"Error: /home/mattycoze/qtoctave/menus not found"

I figure this is because of the new version of Octave. 

Any help would be greatly appreciated!

---

### Post by justus_jonas3 on 2011-03-02
For all those that don't want to install anything to use Octave maybe a browser based editor could be useful. The [Online Octave Editor]("https://www.verbosus.com/") let's you execute Octave code and generate plots from the result. Maybe worth a try...

---

