---
title: "Ubuntu Science Metapackage"
date: 2005-08-30
forum: Education &amp; Science
---

### Post by parktownprawn on 2005-08-30
I was happy to see that the   [Science Dissemination Unit](http://sdu.ictp.it/os/ubuntu.html) at the International Centre for Theoretical Physics is handing out Ubuntu CDs.  
Beside myself I know there are also other researchers  using Ubuntu [http://www.ubuntuforums.org/showthread.php?t=29919](http://www.ubuntuforums.org/showthread.php?t=29919).
 
So.....
I think it would be useful to make a ubuntu science metapackage that would reproduce something like the functionality of  [Quantian](http://dirk.eddelbuettel.com/quantian.html) which is a Knoppix based distribution  tailored to numerical and quantitative analysis. (or possibly other metapackages aimed at different specialities - Ubuntu4Physics, Ubuntu4Chemisty, Ubuntu4Biology etc.)

Then it would just take a single apt-get command to install all the programs you might need to do research under the umbrella of ubuntu/debian goodness. (something like what kubuntu does for kde or what edubuntu does for schools).

So I have two questions  to the comunity

1. How does one create a meta-package ?

2. What packages would be useful for the Scientists/Engineers out there?

I just started a wikki page to list packages that people suggest in case I or anyone else gets round to making such a metapackage: [Ubuntu Science Packages](http://wiki.ubuntu.com/UbuntuSciencePackages)

---

### Post by kanem on 2005-08-30
Excellent idea!

To make a meta-package you just need to make a deb package that has the packages you want included listed as dependencies.

I've uploaded the folder for a sample meta-package. It only has a 'sample-metapackage/DEBIAN/control' file. If the dependencies in this file were replaced  with the packages you want included apt-get would install those when you install the metapackage.

To turn these files into a .deb package just ```
sudo dpkg --build sample-metapackage
```Make sure to not have the trailing / after the 'sample-metapackage'.

My first suggestion to go into the meta package would be [Qalculate!](http://www.gnomefiles.org/app.php?soft_id=106), which I've put as a dependency in the sample meta-package.

---

### Post by parktownprawn on 2005-08-30
[QUOTE=kanem]
To make a meta-package you just need to make a deb package that has the packages you want included listed as dependencies.
[/QUOTE]
thanks alot - thats really easy and whats more it worked  (and qalculate *is* pretty cool).

---

### Post by johanvdw on 2005-08-30
R should definitely make it to the list as well. In every science package!
package names:
r-base
r-recommended

r-cran-rcmdr might be considered as well, to create a gui.

website:
[http://www.r-project.org](http://www.r-project.org)

---

### Post by macgyver2 on 2005-08-30
My $.02:

I have never liked meta-packages and I never will.  I will always prefer simply selecting what I use and passing over what I don't.  I see no reason to use a meta-package and have a bunch of programs I never use hanging around...which could be quite a few if every package everyone suggests is included in the meta-package.  And if every package everyone suggests isn't included, then those people still have to install those packages themselves if they want them...

That being said, I really like the wiki page thing.  It would be great if we could get all the packages from that other thread onto the wiki page.

---

### Post by parktownprawn on 2005-08-31
[QUOTE=macgyver2]My $.02:

I have never liked meta-packages and I never will.  I will always prefer simply selecting what I use and passing over what I don't.  I see no reason to use a meta-package and have a bunch of programs I never use hanging around...[/QUOTE]

i see your 2 cents and raise you 90 paise.

I can understand your aversion to a mega-meta-package - one of the nice things about ubuntu is the clean simple desktop which is bloatware free.

but 

I think meta-pacakages are a great way to customise a linux distribution for specific needs.  For example, rather than teachers having to tweak ubuntu themselves they can just apt-get edubuntu. (Also - as I understand it each version of ubuntu starts out life as a customised version of Debian Unstable  each 6 months ).

Suppose I wish to install a customised version of ubuntu on many desktops/laptops in a particular research environment - it would be very convenient to just have to install one meta-package and let apt do its magic. 

Some people enjoy tweaking their software but for others it may easier to install a well designed meta-package.

Maybe  what we need is a family of meta-packages - a modular meta-verse of Ubuntu Science meta-packages which would give users more choice than a mega-meta-package. 

Having said that, if i get the time, now that i know how to make meta-packages,  drunk with power I'll try write a script to make an ubuntu-quantian  (mega) meta-package which will include all the packages that are common to ubuntu and  [quantian](http://dirk.eddelbuettel.com/quantian.html). 
(Sounds like a sure fire way to break my ubuntu box but it could be fun)

---

### Post by macgyver2 on 2005-08-31
[QUOTE=parktownprawn]Some people enjoy tweaking their software but for others it may easier to install a well designed meta-package.[/QUOTE]
Yes, you have a point there.  I guess since I moved to Ubuntu after nearly 3 years of Gentoo I sometimes forget that not everyone wants to spend a significant percentage of their computer time tweaking things :).

Now, I don't know too much about packaging yet as I've just started trying to teach myself how to do it...so I don't know how feasible this idea is.  What would you think about a preconf script that asks about what packages should or should not be installed.  Now, I realize it would be silly to ask about *every* package in the meta-package...I was thinking about just the larger ones like cernlib, grass, R, octave...

Is it even possible to choose packages on the fly like that?

---

### Post by parktownprawn on 2005-09-01
[QUOTE=macgyver2]
Now, I don't know too much about packaging yet as I've just started trying to teach myself how to do it...so I don't know how feasible this idea is.  What would you think about a preconf script that asks about what packages should or should not be installed.  Now, I realize it would be silly to ask about *every* package in the meta-package...I was thinking about just the larger ones like cernlib, grass, R, octave...

Is it even possible to choose packages on the fly like that?[/QUOTE]

Well I don't know much about packaging either - thats part of the reason I started this thread. I think you could incorporate a preconf script like mentioned into a meta-package.

Personally I would prefer to make modular meta-packages. That would allow you to install particular subsets of the programs rather than the whole lot if you so desire. 

If you wanted more fine grain control you might as well just install all the packages you want individually.

Anyway [CDD tool (customising debian tool)](http://wiki.debian.net/?action=revisions&page_name=CDDTool&revision_id=5) looks like it may be a useful tool for meta-packaging.

People working on kubuntu and edubuntu may be able to offer some advice on the best way to go about this.

---

### Post by phen on 2005-09-01
hello ppl!

the last days something went through my head over and over. there are so many linux sites: desktoplinux, linuxonlaptops linuxgaming linux everything BUT science-on-linux!

a metapackage would be interesting, but: there are too much sciences out there! i am an engineer and dont need tools to organize my insects :-)

so my idea is: lets make a different metapackage for each field of science! but even more interesting would be a website (maybe a wiki in the beginning?), so that everybody could browse through a list of tools for, let's say, maths. there could be reviews, a help forum (for switching from matlab to octane or scilab :-)

there are allready some pages which point to science apps, but none of them seem to be up to date or complete. the page has to have a wiki, so that users could help filling it with content. 

what do you think?


edit: there is a science page, but it is rather small:
[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

edit2: ui:-) ptprawn, it was you who pointed me to that site months ago :-)

---

### Post by ssam on 2005-09-01
please add any science related infomation to the [Ubuntu Scientists](http://www.ubuntulinux.org/wiki/UbuntuScientists) wiki page.

i asked the forum guys if we could have a forum page, but have had no response.

a metapackage may be more trouble than its worth. i dont really want to install loads of statistical and bioinformatic stuff just to get latex and octave. maybe a set of metapackages

ubuntu-scientists-maths
ubuntu-scientists-chem

etc

maybe we should talk to the people doing the add/remove programs system. it might be possible to put a science section in there.

sam

---

### Post by macgyver2 on 2005-09-01
[QUOTE=ssam]i asked the forum guys if we could have a forum page, but have had no response.[/QUOTE]
That would be cool.  There are quite a few scientists or wannabe scientists (a.k.a. engineers ;-)) on here.  A separate forum section would be nice.  A combination of topics like this and random chat topics--for instance I'd be interested in hearing about research projects others are working on, if they want to present them.

---

### Post by parktownprawn on 2005-09-02
[QUOTE=ssam]
a metapackage may be more trouble than its worth. i dont really want to install loads of statistical and bioinformatic stuff just to get latex and octave. maybe a set of metapackages

ubuntu-scientists-maths
ubuntu-scientists-chem

etc
[/QUOTE]

A set of metapackages is probably better in many cases. It would require people from various specialities saying what packages they would like in their meta-package.

So if you know what packages you would like for *your* speciality go to you can put them on the wiki page [UbuntuScienceMetaPackages](http://wiki.ubuntu.com/UbuntuScienceMetaPackages)   

On the other hand it might be useful for people who want to set up a number of ubuntu wokstations which may be used by many different people with different needs to have a larger meta-package. Something like an ubuntu verion of [quantian](http://dirk.eddelbuettel.com/quantian.html). Besides interdisciplinary  research is very fashionable and a sure fire way to improve your funding prospects.

.......

on a lighter note  a tautological song about ["scientific fact" ](http://www.thetalentshow.org/music/scientific_fact-32.mp3)

---

### Post by parktownprawn on 2005-09-03
Just for fun I made a mega-meta package which contains packages common to ubuntu-hoary and [quantian](http://dirk.eddelbuettel.com/quantian.html).

It just took some a bit of "sed" and "comm" - a lot easier than making something from scratch.

Then i removed the packages that conflicted with ubuntu-desktop (and a few games) and  we have ubuntu-quantian (deb package and source attached below).

It also installs kubuntu since quantian is based on a kde-desktop.

Its just an experiment (in progress) and I'm posting it here for people who may want to play around too. 

As people have suggested, I think its a better idea to make some specialised packages for various disciplines but it was just easier to steal some of the work done to make quantian.

It will install a very large number of packages and in fact  I haven't had the guts to install it on my own computer since there is a good chance 
[SIZE=4][COLOR=Red] it will serious break things.[/COLOR][/SIZE] 
It will probably install far more packages than you could ever want. I'll try it out when i get my hands on a machine that I don't mind breaking to test it out. 

If anyone has the some free time, guts  and a system to play around with let me know how it turns out. 

Don't complain to me if this package does something [COLOR=Red]nasty[/COLOR] to your computer.

---

### Post by LaserJock on 2005-09-05
Hi all! 
  I just wanted to throw in my $0.05 (inflation  :roll: ). I think that it would be difficult to  add science meta packages. For one, we would probably need to make several meta packages (meta-science-math, meta-science-physics, meta-science-chemistry, meta-science-biology, meta-science-statistics, etc.) and we would have to "decide" what packages to include in both. I think a better direction would be to work more on the [UbuntuScientists](http://wiki.ubuntu.com/UbuntuScientists)  wiki page and provide a simple one line "apt-get" command that would install what most users would  want for each discipline. That way, it is a simple, one-line copy & paste but the users can also tailor it by adding what they want without being locked into specific packages (like with a meta-package). Its not "all or nothing".
  I think that good documentation would alleviate a lot of the need for these meta packages.

-LaserJock (JordanMantha)

---

### Post by phen on 2005-09-06
good idea! better result with less work :-)

---

### Post by parktownprawn on 2005-09-12
[QUOTE=LaserJock].... we would probably need to make several meta packages (meta-science-math, meta-science-physics, meta-science-chemistry, meta-science-biology, meta-science-statistics, etc.) and we would have to "decide" what packages to include in both. I think a better direction would be to work more on the [UbuntuScientists](http://wiki.ubuntu.com/UbuntuScientists)  wiki page and provide a simple one line "apt-get" command that would install what most users would  want for each discipline. That way, it is a simple, one-line copy & paste but the users can also tailor it by adding what they want without being locked into specific packages (like with a meta-package). Its not "all or nothing".
[/QUOTE]

I agree that getting a good list of packages is the most important part.

I did some editing of the page
[Ubuntu Science Metapackages](https://wiki.ubuntu.com/UbuntuScienceMetaPackages) 
to suggest that people can use "apt-get" and cut and paste packages. This is probably a convenient method for many people.

Everyone - please add/edit this page as you see fit.

---

### Post by parktownprawn on 2005-09-14
It turns out there are *already* some science metapackages in Ubuntu - from [Debian-Med](http://www.debian.org/devel/debian-med/) for doctors and medical researchers.

to list the meta-packages type```
apt-cache search debian-med 
```

---

### Post by ajt on 2009-01-21
> **ssam said:**
> please add any science related infomation to the [Ubuntu Scientists](http://www.ubuntulinux.org/wiki/UbuntuScientists) wiki page.
[...]


Hello, Sam.

That page does not exist!

I've added a link to Bio-Linux 5.0 at:

[https://help.ubuntu.com/community/UbuntuScience/Biology]("https://help.ubuntu.com/community/UbuntuScience/Biology")

Bye,

Tony.

---

### Post by ssam on 2009-01-22
hi.
this thread is quite old. the page has now moved to 
[https://help.ubuntu.com/community/UbuntuScience](https://help.ubuntu.com/community/UbuntuScience)

---

### Post by ajt on 2009-01-22
Hello, Sam.

Thanks for replying to my post on the Ubuntu Education and Science
Forum: I notice that you are a PPC fan  :-) 

I've got an iLamp with 8.10 on it - Have you any experience of using
QtNX under Ubuntu for the PPC?

Bye,

        Tony.

---

