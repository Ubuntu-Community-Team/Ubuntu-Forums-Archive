---
title: "Scientific Software options for Ubuntu"
date: 2006-03-25
forum: Education &amp; Science
---

### Post by akniss on 2006-03-25
At MIPS suggestion:
A place to tell others about software that you have found to be useful in scientific fields.  Feel free to post your useful scientific software packages, and I will try to keep this first post up to date with your suggestions.


**Statistics:**
*R*
[http://www.r-project.org/](http://www.r-project.org/)  
```
sudo aptitude install r-recommended
```


**LaTeX editors:**
*Lyx*
[http://www.lyx.org/](http://www.lyx.org/)
```
sudo aptitude install lyx
```
*Kile*
[http://kile.sourceforge.net/](http://kile.sourceforge.net/)
```
sudo aptitude install kile
```
*TeXmaker*
[http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)
```
sudo aptitude install texmaker
```

**Bibtex:**
*Pybliographer*
[http://sourceforge.net/projects/pybliographer/](http://sourceforge.net/projects/pybliographer/)
```
sudo aptitude install pybliographer
```


**Bibliographic Database:**
*Bibus*
[http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page](http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page)
[Installation instructions](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Debian_and_Ubuntu)


**Spreadsheet:**
*Gnumeric*
[http://www.gnome.org/projects/gnumeric/](http://www.gnome.org/projects/gnumeric/)
```
sudo aptitude install gnumeric
```


**Desktop Publishing:**
*Scribus*
[http://www.scribus.net/](http://www.scribus.net/)
```
sudo aptitude install scribus
```


**GIS:**
*GRASS*
[http://grass.itc.it/](http://grass.itc.it/)
```
sudo aptitude install grass
```

*QGIS*
[http://qgis.org/](http://qgis.org/)
```
sudo aptitude install qgis
```

**Mathematics:**
*Scilab*
[http://www.scilab.org/](http://www.scilab.org/)
```
sudo aptitude install scilab
```
Some users have had issues with text showing up only in Hindi when installing scilab from the Ubuntu repos.  There is a binary version available on the scilab website. Just unpack it and read the README_Unix file.

*Maxima*
[http://maxima.sourceforge.net/](http://maxima.sourceforge.net/)
```
sudo aptitude install maxima
```

*Octave*
[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)
```
sudo aptitude install octave
```

---

### Post by Barrakketh on 2006-03-25
You could consider giving Kile a try for LaTeX.  It's rather nice.

---

### Post by ssam on 2006-03-25
there is also some good info on [https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

i am looking forward to having a science forum :-)

---

### Post by towsonu2003 on 2006-03-25
I would (unfortunately) add qemu for those who have no time to learn a new program and need solution right away (thus using Windows)... again, unfortunately. 

PS. SPSS => R != GUI => qemu + keku + SPSS

---

### Post by LadyDoor on 2006-03-25
Hey! None of you Ubuntu scientists would happen to be *social* scientists, would you? And if you are (or not) would you happen to know how to get the latest version of PSPP from CVS? When I do the first step described in their instructions (make -f Smake) it works for a while, then prints out a lot of commented "include" statements, and then the following:

```
Don't forget to
  - add "gl/Makefile" to AC_CONFIG_FILES in ./configure.ac,
  - mention "gl" in SUBDIRS in Makefile.am,
  - mention "-I gl/m4" in ACLOCAL_AMFLAGS in Makefile.am,
  - invoke gl_EARLY in ./configure.ac, right after AC_PROG_CC,
  - invoke gl_INIT in ./configure.ac.
autoreconf --install
aclocal: configure.ac: 12: macro `AM_PROG_CC_C_O' not found in library
autoreconf: aclocal failed with exit status: 1
make: *** [all] Error 1
```

Does anybody know how to fix this problem with what could be very good scientific software?

---

### Post by neoflight on 2006-03-25
[QUOTE=Barrakketh]You could consider giving Kile a try for LaTeX.  It's rather nice.[/QUOTE]


a how to for texmaker and kile with texlive in my signature.... :mrgreen:  
even some instructions on getting kile from source without tetex ....:KS

---

### Post by akniss on 2006-03-26
I just got Bibus working also by following the howto at this thread:
[http://www.ubuntuforums.org/showthread.php?t=122841&highlight=bibus](http://www.ubuntuforums.org/showthread.php?t=122841&highlight=bibus)

---

### Post by derjames on 2006-04-06
Hi there, 
For those interested in physical/chemical modelling I did find an open source multiphysics package similar to COMSOL (formerly FEMLAB), I haven't compiled yet, however I will work on this shortly, The name of the package is ELMER, developed by a Finnish institute, there are binaries for download for Win32, Linux RPM, Mac, etc... the source code is available to download as well.

Hope this helps

[http://www.csc.fi/elmer/index.phtml](http://www.csc.fi/elmer/index.phtml)

---

### Post by akniss on 2006-04-09
Has anyone used or tried the ChemicalInventory package listed on the Science Wiki?  Just curious if it is functional enough to warrant giving it a try...

---

### Post by mips on 2006-04-10
People, have a look at this:

[http://www.openchannelfoundation.org/](http://www.openchannelfoundation.org/)
[http://www.openchannelfoundation.org/cosmic/](http://www.openchannelfoundation.org/cosmic/)

Please note that the above is NOT free but could prove valuable to some people.

---

### Post by ericsp on 2006-04-26
Re: Akniss and the R-project.

I see the power of the R-project, but the interface is horrible. Is there anyone working on a good interface?

---

### Post by akniss on 2006-04-26
[QUOTE=ericsp]Re: Akniss and the R-project.

I see the power of the R-project, but the interface is horrible. Is there anyone working on a good interface?[/QUOTE]


I suppose that really depends on what you are used to.  In my field, SAS is the standard.  This makes the switch to R rather easy, as they both have a command-line programming language feel to them.  Most people who feel as you do typically come from Minitab or SPSS or... Excel *shudder*.  The learning curve is steep; however coming from SAS I've really enjoyed the transtition.  I can make a plot in R with two or three lines of code that would take me a page and a half of code in SAS.  However, two or three lines of code is two or three too many for those used to pointing and clicking their way around Minitab or SigmaPlot.  

The true "power of the R-project" really comes from the fact that it is a full progamming language.  We are not limited to a set of default analysis methods which may or may not be appropriate for the data.  I have written a few functions in R that allow me to create detailed diagnostic plots with a one-line command.  This sort of thing is just not possible with 95% of commercial gui-based statistical packages.  It can be cumbersome at times when one only wants to perform simple analyses or transformations on a data set; but if this is all you want out of a statistical package, then R is probably not for you anyway.  Any attempt at simplifying the interface to point and click will necessarily take away functionality, as there is no way to incorporate all the functionality of R into a few context menus.

With all that being said, there are a few projects out there that have put a gui interface on top of R.  Rcmdr is available in the Ubuntu repos and does an ok job.  The one that looks the most exciting in my opinion is JGR (pronounced Jaguar).  It is java based and so platform independent.  I have not personally tried it but have heard good things.

---

### Post by Kyle- on 2006-04-26
[QUOTE=ericsp]Re: Akniss and the R-project.

I see the power of the R-project, but the interface is horrible. Is there anyone working on a good interface?[/QUOTE]

This is by far the most promising thing I've seen.  [http://kde-apps.org/content/show.php?content=14880]("http://kde-apps.org/content/show.php?content=14880")  

You can also install a GUI called Rcmdr within R.  Just connect to an R reposititory, install the package, and at the input prompt type

```
library(Rcmdr)
```

It's not the prettiest thing in the world, but it's stable.  

One other thing.  I've recently begun experimenting with using DOSbox to run an old DOS version of Kwikstat.  It works well after some fiddling with the install (edit a script so it Kwikstat doesn't look for a printer on install).  This might be an option for those of you who are still using older software.  I find Kwikstat quite satisfactory for most things.  

Aside from statistics, I use CXoffice to run Endnote.  I just cant switch.  There is a Linux version of Maple, so no problem there.  Maxima is also a decent free computer algebra system. 

I really wish someone could get a recent versionn of SPSS working in Linux with a GUI.

---

### Post by towsonu2003 on 2006-04-26
[QUOTE=ericsp]
I see the power of the R-project, but the interface is horrible.[/QUOTE]
check out this: [https://stat.ethz.ch/pipermail/r-devel/2006-March/036728.html](https://stat.ethz.ch/pipermail/r-devel/2006-March/036728.html)

This is a bug (or, rather, a feature request) I filed a while ago. You will find your response in devels' replies to my bug report / feature request......

---

### Post by claudine on 2006-04-26
I'm forced to use Stata at work but I'd like to learn R. Do you think going from Stata to R would require a huge mental leap?

---

### Post by akniss on 2006-05-03
[QUOTE=claudine]I'm forced to use Stata at work but I'd like to learn R. Do you think going from Stata to R would require a huge mental leap?[/QUOTE]

I don't know much about Stata... From looking at their website, it looks like it is predominantly a command based package as well.  (I'm actually kind of interested in playing around with Stata now!)  I think the switch to R is much easier for those of us who are already used to typing in commands to get means, regressions, and box plots.

However, learning any new language is frustrating at times.  It took me a couple years to learn SAS to the point that I was reasonably proficient, and it was difficult to transition from the proc ****; world over to the function() world.  I gave up a few times, but eventually got the hang of it and am now much more efficient in R.

---

### Post by akniss on 2006-05-03
[QUOTE=Kyle-]This is by far the most promising thing I've seen.  [http://kde-apps.org/content/show.php?content=14880]("http://kde-apps.org/content/show.php?content=14880")  

[/QUOTE]

Kyle, that looks fantastic!  I hadn't heard of it yet.  I suppose the chances of it getting into the Dapper repos are null...

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=akniss]Kyle, that looks fantastic!  I hadn't heard of it yet.  I suppose the chances of it getting into the Dapper repos are null...[/QUOTE]
try suggesting it to the backports (there is a forum section for that). Let us know of the thread link so we can support.

---

### Post by claudine on 2006-05-03
[QUOTE=akniss]I don't know much about Stata... From looking at their website, it looks like it is predominantly a command based package as well.  (I'm actually kind of interested in playing around with Stata now!)  I think the switch to R is much easier for those of us who are already used to typing in commands to get means, regressions, and box plots.

However, learning any new language is frustrating at times.  It took me a couple years to learn SAS to the point that I was reasonably proficient, and it was difficult to transition from the proc ****; world over to the function() world.  I gave up a few times, but eventually got the hang of it and am now much more efficient in R.[/QUOTE]

Yes, Stata is very much command-driven. I'm writing Stata scripts in Emacs with ESS mode. Stata mostly does what I need, but it's not free (my philosophical objection). And all the statisticians at work use it and seem to think R is too "difficult". It seems the main issues with R are its object-oriented nature and syntax.

---

### Post by akniss on 2006-05-03
[QUOTE=claudine]Yes, Stata is very much command-driven. I'm writing Stata scripts in Emacs with ESS mode. Stata mostly does what I need, but it's not free (my philosophical objection). And all the statisticians at work use it and seem to think R is too "difficult". It seems the main issues with R are its object-oriented nature and syntax.[/QUOTE]


R certainly does have a cryptic syntax... however, I would argue that there is nothing more cryptic than Emacs ](*,) , so if you've mastered that...  ESS is also able to interface with R, so I think it wouldn't be too terrible a transition for you.  I gave ESS a whirl a few months ago and just coulnd't get hooked.  I thought it was ok, but decided KDE's kate editor was better suited for my needs.  I guess there's only one way to find out: install it and give it a try.  Just take it slow and don't think you'll be able to master it the first few times.  If you're anything like me, it will take a while to 'unlearn' your other language (It took me about a month to stop putting a semi-colon at the end of each line).  Good luck, and if you have trouble getting started there are pretty good books, online help, and documentation available.  And I'm sure there are a few R junkies on this forum besides myself as well!

---

### Post by akniss on 2006-09-12
I've just installed scilab and am starting to play around with it.  Does anyone know of a good noob-level tutorial for scilab?

---

### Post by akniss on 2006-09-26
> **akniss said:**
> I've just installed scilab and am starting to play around with it.  Does anyone know of a good noob-level tutorial for scilab?

To answer my own question, here is one quick and dirty tutorial that has gotten me started.
[http://www.scilab.org/doc/intro/node7.html](http://www.scilab.org/doc/intro/node7.html)

I was quite happy to learn that the Emacs commands work at the scilab command line!  All that time spent learning ESS has finally paid off!

---

### Post by philyer on 2006-11-06
**Maxima**
A powerful symbolic caculation tool, like *Mathematica*.

---

### Post by adamkane on 2006-11-09
Lyx and Maxima can be combined to create a very good report writer and equation solver:

Lyx + Maxima
[http://www.jstatsoft.org/v17/s01/v17s01.pdf](http://www.jstatsoft.org/v17/s01/v17s01.pdf)

---

### Post by Steve Pullman on 2006-11-17
Zhu3D is a very nice opengl surface plotter

[http://www.kde-apps.org/content/show.php?content=43071](http://www.kde-apps.org/content/show.php?content=43071)

I had to compile it (it isn't in the repository), but it wasn't troublesome.

---

### Post by abarth on 2006-11-28
Octave is very well suited for numerical computations. Its syntax is quite easy to learn and it is mostly compatible with Matlab.

[http://www.octave.org](http://www.octave.org)

---

### Post by adamkane on 2006-11-30
Can anyone describe how they got octave-workshop installed on Ubuntu?

[http://www.math.mcgill.ca/loisel/octave-workshop/](http://www.math.mcgill.ca/loisel/octave-workshop/)
[http://www.math.mcgill.ca/loisel/octave-workshop/octave-workshop-0.7/doc/install.html](http://www.math.mcgill.ca/loisel/octave-workshop/octave-workshop-0.7/doc/install.html)

---

### Post by slimdog360 on 2006-11-30
You may want to add the octave-forge package to that list.

---

### Post by adamkane on 2006-12-02
I downloaded octave-workshop:
[http://www.math.mcgill.ca/loisel/octave-workshop/octave-workshop-0.10.tar.gz](http://www.math.mcgill.ca/loisel/octave-workshop/octave-workshop-0.10.tar.gz)

octave is already installed.

octave-workshop requires QT4.1, so you need to install QT4, then install QT4.1 from source:
[https://help.ubuntu.com/community/BuildingQuantumGisPoint8FromSource](https://help.ubuntu.com/community/BuildingQuantumGisPoint8FromSource)
[http://openmodeller.cria.org.br/wikis/omgui/LinuxBuildInstructions](http://openmodeller.cria.org.br/wikis/omgui/LinuxBuildInstructions)

QT4:
```

sudo apt-get install libqt4-core libqt4-debug libqt4-debug-dev libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql lsb-qt4 qt4-designer qt4-dev-tools qt4-doc qt4-qtconfig uim-qt gcc libapt-pkg-perl resolvconf

```QT4.1:
```

sudo apt-get install libxrender-dev libxrandr-dev libxcursor-dev libxinerama-dev libfontconfig-dev libxext-dev libx11-dev libxi-dev libsm-dev libx11-dev 

``````

mkdir -p $HOME/installers[FONT=monospace]
[/FONT]cd ~/installers[FONT=monospace]
[/FONT]wget ftp://ftp.trolltech.com/qt/source/qt-x11-opensource-src-4.1.0.tar.gz[FONT=monospace]
[/FONT]tar xfz ~/installers/qt-x11-opensource-src-4.1.0.tar.gz[FONT=monospace]
[/FONT]cd qt-x11-opensource-src-4.1.0

``````

/configure -prefix /usr/local/Trolltech/Qt-4.1.0 [FONT=monospace]
[/FONT]make [FONT=monospace]
[/FONT]sudo make install

```I then tried to install octave-workshop from source, but I got this error:
> 
checking whether we can build a liboctave program... configure: error: Cannot link against liboctave
I don't think there is a solution to this error without recompiling octave-workshop, which is beyond my ability.

QT4.1 is installed, so we can try another method. Convert the RPM file to a DEB file.

I downloaded the octave-workshop RPM to my desktop:
[http://webpages.charter.net/qspencer/rpm/](http://webpages.charter.net/qspencer/rpm/)

I converted the RPM to a DEB:
```

cd ~/Desktop
sudo alien -d octave-workshop-0.10-1.i386.rpm

```The RPM file uses termcap, but the DEB file requires ncurses:
[http://directory.fedora.redhat.com/wiki/Howto: DebianUbuntu]("http://ubuntuforums.org/%22http://directory.fedora.redhat.com/wiki/Howto:DebianUbuntu%22")

so you need to download these old breezy DEB files to install octave-workshop in dapper:

termcap-compat
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ft%2Ftermcap-compat%2Ftermcap-compat_1.2.3_i386.deb&md5sum=65eaae25cd8382a193b416428617bc79&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ft%2Ftermcap-compat%2Ftermcap-compat_1.2.3_i386.deb&md5sum=65eaae25cd8382a193b416428617bc79&arch=i386&type=main)

libc5
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Flibc%2Flibc%2Flibc5_5.4.46-15_i386.deb&md5sum=e8fffc5b3bfb9b1d716a93e764547baa&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Flibc%2Flibc%2Flibc5_5.4.46-15_i386.deb&md5sum=e8fffc5b3bfb9b1d716a93e764547baa&arch=i386&type=main)

ldso
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fl%2Fld.so%2Fldso_1.9.11-15_i386.deb&md5sum=53caec6628874f687137d242a6adbc42&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fl%2Fld.so%2Fldso_1.9.11-15_i386.deb&md5sum=53caec6628874f687137d242a6adbc42&arch=i386&type=main)

You then need to create a link for libhdf5.so.0:
```

cd /usr/lib
sudo ln -s libhdf5-1.6.4.so.0 libhdf5.so.0

```I then get this error when I ran octave-workshop:
> 
*** glibc detected *** free(): invalid pointer: 0x08c90cb0 ***
Aborted
That's as far as I got.

I then uninstalled the breezy DEB files, and removed the libhdf5.so.0 link:
```

cd /usr/lib
sudo rm libhdf5.so.0

```

---

### Post by maystar on 2006-12-05
hello just trying out ubuntu forums!!

---

### Post by Toufik on 2007-01-09
I went further with less step :D

Install QT4
$ sudo apt-get install libqt4-core lib-qt4-dev

Download RPM
$ wget [http://webpages.charter.net/qspencer/rpm/octave-workshop-0.10-1.i386.rpm](http://webpages.charter.net/qspencer/rpm/octave-workshop-0.10-1.i386.rpm)

Convert into .deb
$ sudo dpkg -d octave-workshop-0.10-1.i386.rpm

Install it
$ sudo dpkg -i octave-workshop-0.10-1.i386.deb

Then try it: 
$ octave-workshop

You get libtermcap error --> search for it ($ locate libtermcap) --> it only changes name so make a symbolic link
$ sudo ln -s /usr/lib/libtermcap.so /usr/lib/libtermcap.so.2

Now, I'm stuck with liboctinterp.so
> octave-workshop: error while loading shared libraries: liboctinterp.so: cannot open shared object file: No such file or directory

But I've of course the liboctinterp.so in /usr/lib/octave-2.1.73/liboctinterp.so  I guess the binary is looking at th wrong place... don't know how to correct this.  I've put symbolic link everywhere... nope

Pffff

---

### Post by cuonght on 2007-01-09
I am very interested in IFEFFIT software, but I don't know how to install this soft ware in my computer. Here is a link for this
[http://cars9.uchicago.edu/ifeffit/download.html](http://cars9.uchicago.edu/ifeffit/download.html)

Can someone help me to install it? thanks a lot!

---

### Post by Toufik on 2007-01-09
Just follow the instructions here :
[http://cars9.uchicago.edu/ifeffit/src/INSTALL](http://cars9.uchicago.edu/ifeffit/src/INSTALL)

Rmq: You'll need that first
```
$ sudo apt-get install build-essential
```

Basically, when you get source in .tar.gz format:
1) decompress the archive and enter the new directory
```
$ tar -xzvf xxxx.tar.gz
$ cd xxxx
```
2) configure the building and installation
```
$ ./configure
```
You should get messages telling if it is OK or not. In that last case, look at the problem and try to correct it by installing the missing software via apt-get.  For instance, if it tells you that yyyyy is missing, then look for it:
```
$ apt-cache search yyyyy
```
You'll get some answer(s) (if not then look in the forum), let's say abcdef.  Then install it via
```
$ sudo apt-get install abcdef
```
and start point 2 again.

3) When it finished ok, you can build the program:
```
$ make
```
Here also, you'll get a lot of messages, if there is a problem, look in the forum.  At the end, you'll get a binary

4) Install the binary
```
$ sudo make install
```
And everything should be working and located at the right place (you can safely remove xxxx.tar.gz and the directory xxxx).  To execute, type the name of the program.

Rmq: there is always (at least) one problem when installing from source... always look for a .deb first

---

### Post by cuonght on 2007-01-10
thanks for your instruction. But I still got a problem, that is, after configure, it informs an error as following:
===
===  ifeffit 1.2.8 Configuration Results:
===  linking to PGPLOT with: /home/htcuong/Desktop/ifeffit-1.2.8/src/pgstub/libnopgplot.a
===
===  could not find TERMCAP Libraries : 'make' will fail.
===
===  Please set TERMCAP_LIB in src/cmdline/Makefile or use the
===  --termcap-link argument before running make

Do you know what it is? thanks

---

### Post by Toufik on 2007-01-11
termcap is now replaced by ncurses but I don't know which packages exactly.  Try to install some packages containing ncurses (probably ncurses-base, ncurses-bin and ncurses-term)

If you experience problem with an installation: open a new forum!  You'll get more help with a precise title!

---

### Post by olejorgen on 2007-01-15
> **Steve Pullman said:**
> Zhu3D is a very nice opengl surface plotter

[http://www.kde-apps.org/content/show.php?content=43071](http://www.kde-apps.org/content/show.php?content=43071)

I had to compile it (it isn't in the repository), but it wasn't troublesome.
Does anyone know of a program like this (that support implict 3d plots) for gnome?

---

### Post by sureinlux on 2007-02-21
[RLPLot]("http://rlplot.sourceforge.net") is a great WYSIWYG plotting software with a shallow learning curve. Available in the repos and great for publication quality graphs.

---

### Post by slaanco on 2007-02-21
many astronomical codes that can be run on ubuntu can be found [here]("http://en.wikiversity.org/wiki/Astrophysics_Source_Code_Library")

---

### Post by Timtro on 2007-03-13
> **Barrakketh said:**
> You could consider giving Kile a try for LaTeX.  It's rather nice.

TeXmaker is nice too. I hear it's from the guy who started the Kile project. There are some differences, but Texmaker loads a--lot--faster.

---

### Post by Cellular on 2007-03-28
gretl is a great package for econometrics and time series analysis. It also has some simple tools for finding p-values and doing elementary t-tests etc. It has a very easy-to-use GUI as well as a command line interface, it is easy (from what i've heard) to extend with scripts, and it can send it's data to R. 

It produces plots with Gnuplot, and you can get it's output in latex format.

[http://gretl.sourceforge.net/]("http://gretl.sourceforge.net/")

---

### Post by tomasz2006 on 2007-04-12
> **Cellular said:**
> gretl is a great package for econometrics and time series analysis. It also has some simple tools for finding p-values and doing elementary t-tests etc. It has a very easy-to-use GUI as well as a command line interface, it is easy (from what i've heard) to extend with scripts, and it can send it's data to R. 

It produces plots with Gnuplot, and you can get it's output in latex format.

[http://gretl.sourceforge.net/]("http://gretl.sourceforge.net/")

I agree with the above, the main strength of gretl is its easy-to-use and friendly interface. Also, the export of output to LaTeX might be of interest. 

I add a little ``installing gretl HOWTO'' which I wish had existed when I tried to install it. gretl has some `non-standard' dependencies but luckily the following command helps a lot (worked perfectly on Edgy Eft):

```
apt-get build-dep gretl
```

Then, download the source package from 

[http://gretl.sourceforge.net/](http://gretl.sourceforge.net/)

Decompress the archive and enter the new directory. Then, execute, one by one, the following:

```
./configure
```
```
make
```
```
sudo make install
```

Hopefully, everything goes smoothly and gretl is installed. In case you wonder, the above procedure did NOT work with the checkinstall. I hope this helps.

---

### Post by vinx on 2007-04-20
It is easier to compile Octave Workshop for Actave 2.9 on Fiesty, since the newest QT4-libs are included. You'll need to make one edit before compiling.

Install the following packages (and dependecies):
```

qt4-dev-tools
octave2.9-headers
libreadline5-dev

```

Just download the tar.gz from [http://www.math.mcgill.ca/loisel/octave-workshop/]("http://www.math.mcgill.ca/loisel/octave-workshop/") , unpack and add the following as line 11 to the file 'editwindow.cpp':
```
#include <assert.h>
```

Now it's time for a './configure' , which should give no errors.
now do a 'make'. If you did not make the edit to editwindow.cpp, it complains about 'assert' not being defined.

Few moments later you have a 3.4mb bunch of working code. Don't forget to install gnuplot and to start the workshop from the shell to see some usefull crash-output.

--
Vincent

---

### Post by kikuhi on 2007-05-02
For quick plotting, check out "gnuplot". It is quite handy and versatile. If anybody know other open source plot tools?

Cheers,
KiKuHi

---

### Post by abarth on 2007-05-04
> **kikuhi said:**
> For quick plotting, check out "gnuplot". It is quite handy and versatile. If anybody know other open source plot tools?

Cheers,
KiKuHi

The python package matplotlib is quite powerful too. Its interface is modeled after the plotting commands of matlab.

Cheers,
alex

---

### Post by guano on 2007-06-23
For thos interested in using the latest stable versions of GIS software (GRASS, GDAL, QGIS), use this repo:

```
deb http://les-ejk.cz/ubuntu edgy multiverse
deb-src http://les-ejk.cz/ubuntu edgy multiverse
```
or
```
deb http://les-ejk.cz/ubuntu feisty multiverse
deb-src http://les-ejk.cz/ubuntu feisty multiverse
```
   
the versions in the official repos are a bit outdated.

As for the Kile x Texmaker, Texmaker loads faster, but Kile has word completion (and tex commands too).

As Reference manager, I use JabRef. Is Java based and very good. I found a .deb somewhere...

If you go to [http://www.getdeb.net]("http://www.getdeb.net"),  you can fin a tool called Extrema, for graphs creation. Sounds good.

---

### Post by hardyn on 2007-07-07
I got octave workshop to compile under feisty...

you must use all the QT 4.1 libs as noted previous in this post (synaptic)
you must install the readline-dev libs (synaptic)
you must intstall the octave-headers (synaptic)
you must edit the "editwindow.cpp" file and add "#include <assert.h>" to the includes, compile error without
then compile using ./config and make
(way too much work)


cheers.

---

### Post by dannemil on 2007-07-09
> **sureinlux said:**
> [RLPLot]("http://rlplot.sourceforge.net") is a great WYSIWYG plotting software with a shallow learning curve. Available in the repos and great for publication quality graphs.

Outstanding! I have been looking for a good open-source, easy to use, gui plotting package for years. [_RLPlot_]("http://rlplot.sourceforge.net/") is it! Thanks for the suggestion.

Jim

---

### Post by Schoappied on 2007-07-12
Hi,

I study Psychology and I work a lot with SPSS. What is the best program in Ubuntu to work with statistics and have the same possibilities which SPSS has?
The program must be able to open SPSS-files if possible...

---

### Post by akniss on 2007-07-12
> **Schoappied said:**
> Hi,

I study Psychology and I work a lot with SPSS. What is the best program in Ubuntu to work with statistics and have the same possibilities which SPSS has?
The program must be able to open SPSS-files if possible...

Sounds like you might want to take a look at [PSPP.]("http://www.gnu.org/software/pspp/")  It might not have the functionality you are looking for yet, but the goal is to have an SPSS-like program eventually.  I think its your best bet for opening SPSS files.  However, if you want a truly powerful statistical program for linux, you should look into [R.]("http://www.r-project.org/")

---

### Post by Schoappied on 2007-07-12
Thanks, I think PSPP can not really compare to SPSS. Tell me if I'm wrong...
I will try R-project...

---

### Post by ibbuntu on 2007-08-15
I like JabRef for managing my references. It's in the repos and can be used with a whole host of different editors. Saves its files in BibTex format and can import many other different reference file formats. It's a Java application, so will run on any operating system too.

---

### Post by kiranbhaskar on 2007-08-30
Dear akniss  nice post :)

---

### Post by glee on 2007-09-09
Emacs + [ESS]("http://ess.r-project.org/") (Emacs Speaks Statistics) is a great interface when using R!!

---

### Post by jjvenkit@uwaterloo.ca on 2007-11-21
Can anyone recommend an alternative to NVivo?

thanks,
jason.

---

### Post by zasf on 2007-12-10
I use geany with great pleasure for programming (ruby and python) and latex. Altough not fancy it is very quick and powerful.

I previously tried bluefish for latex editing but, altough it provides some useful shortcuts, it had worst higlight support than geany.

---

### Post by slimdog360 on 2007-12-26
I dont know if its been mentioned yet but you should put in FreeMat [http://freemat.sourceforge.net/wiki/index.php/Main _Page]("http://freemat.sourceforge.net/wiki/index.php/Main _Page")

---

### Post by myle on 2008-01-17
> **Timtro said:**
> TeXmaker is nice too. I hear it's from the guy who started the Kile project. There are some differences, but Texmaker loads a--lot--faster.

I agree with you. Even if Kile has a better reputation, I think if you ise Gnome, it's better to use TeXmaker.

---

### Post by Xtrmi on 2008-01-30
I need to be able to plot equations in implicit form on my eeepc. Does anybody have any suggestions. Installed Scilab to to what it would do but I dont have the time to figure it out cuz I got to much HW. Also this doesn't belong here but could someone quickly mention a messenger program that works with the camera. Thanks for any help u can provide. Even a web version of the graphing program would work for me. if you know of one. Thanks.

---

### Post by towsonu2003 on 2008-01-30
> **Xtrmi said:**
> I need to be able to plot equations in implicit form on my eeepc. Does anybody have any suggestions. Installed Scilab to to what it would do but I dont have the time to figure it out cuz I got to much HW. Also this doesn't belong here but could someone quickly mention a messenger program that works with the camera. Thanks for any help u can provide. Even a web version of the graphing program would work for me. if you know of one. Thanks.

I don't know what 'implicit form' is, but you can use gnuplot to plot equations, get the output in some image format, and put it in your HW. 
[http://www.gnuplot.info/](http://www.gnuplot.info/)
[http://mathewpeet.org/computing/gnuplot/](http://mathewpeet.org/computing/gnuplot/)

---

### Post by olejorgen on 2008-01-30
Implicit form: x^2 + y^2 = 1

I don't think gnuplot can do this out of the box, but I think I've seen some triks you can do. Can't remember where I saw it though.

---

### Post by Xtrmi on 2008-01-30
Installed it throuh the consol and i can't find it. any hints on where it might be?

---

### Post by marrabld on 2008-03-04
Use Octave to plot your implicit function. <google for help> it will pass you solution to GNUplot.

And on that point can anyone tell me how to change the background colour of plots when using Octave.  For some reason the ubuntu version is set to grey, I need to put my plots into documents and grey is horrible.

I have looked far and wide on the net and cannot find help on this.  I really need to solve it soon or ill be forced to install Octave into windows and i dont want to do that.

Cheers

---

### Post by Moonlit Knight on 2008-03-06
Turn it into parametrics and you can plot it quite well with gnuplot just put:

set parametrics on

That function is a circle just do g(x,y) = (cos u, sen u) 
There it is

---

### Post by rjmoerland on 2008-03-06
I love the combination of jabref (mentioned already in this thread) with subversion. I use subversion a lot to version control my articles, but what I find truely useful is that I can use a single bib file for all my articles, using the 'external' property of subversion. This way, if I edit any checked out copy of the bib file, all the other onces are updated as well. Moreover subversion makes it incredibly easy to work at home and at work on the same text, just commit changes at work, go home, update working copy and continue. 

My 2 cts.

---

### Post by qgfreire on 2008-05-06
OpenFoam FoamX 
[http://www.opencfd.co.uk/openfoam](http://www.opencfd.co.uk/openfoam)
The OpenFOAM (Open Field Operation and Manipulation) CFD Toolbox can simulate anything from complex fluid flows involving chemical reactions, turbulence and heat transfer, to solid dynamics, electromagnetics and the pricing of financial options. OpenFOAM is produced by OpenCFD Ltd, is freely available and open source, licensed under the GNU General Public Licence. 

It's a must for a free version os CFD.
Great forum. But ....

---

### Post by dbulnes on 2008-05-30
Is there Anybody out there using Chimera from UCSF, They have a linux version, but me being new on linux/ubuntu havent been able to make it work. If someone has, please let me know how you did. Thanks a lot!

---

### Post by dbulnes on 2008-05-30
Is there Anybody out there using Chimera from UCSF, They have a linux version, but me being new on linux/ubuntu havent been able to make it work. If someone has, please let me know how you did. Thanks a lot!

---

### Post by jjgomera on 2008-05-30
> **dbulnes said:**
> Is there Anybody out there using Chimera from UCSF, They have a linux version, but me being new on linux/ubuntu havent been able to make it work. If someone has, please let me know how you did. Thanks a lot!

open a terminal

download program:
wget [https://www.cgl.ucsf.edu/cgi-bin/chimera-get.py?file=linux/chimera-1.2470-linux.exe](https://www.cgl.ucsf.edu/cgi-bin/chimera-get.py?file=linux/chimera-1.2470-linux.exe)

make it executable:
chmod -x chimera-1.2470-linux.exe

run it as root
sudo ./chimera-1.2470-linux.exe

it asks install directory, you can let by default /usr/local/chimera/

It's autoinstall program, so it installs all its dependences

Finally for run program:  sh /usr/local/chimera/bin/chimera

If you use 64bits architecture use [https://www.cgl.ucsf.edu/cgi-bin/chimera-get.py?file=linux_x86_64/chimera-1.2470-linux_x86_64.exe](https://www.cgl.ucsf.edu/cgi-bin/chimera-get.py?file=linux_x86_64/chimera-1.2470-linux_x86_64.exe)

PD: thanks for info, i dont know that program, and it looks good:)

---

### Post by UbuWu on 2008-05-31
[URL="http://rkward.sourceforge.net/"]Rkward
[/URL] is a great alternative to spss.

Also there is a more comprehensive list on the wiki:
[https://help.ubuntu.com/community/UbuntuScience](https://help.ubuntu.com/community/UbuntuScience)

---

### Post by Guillex on 2008-09-09
Perdon que no escriba en ingles.

Se llama *librarian*

[http://www.bioinformatics.org/librarian/index.php]("http://www.bioinformatics.org/librarian/index.php")

Para todo aquel que investigue... recomiendo que vean el link

no lo he probado aun.

---

### Post by mips on 2008-09-10
> **Guillex said:**
> Perdon que no escriba en ingles.

Se llama *librarian*

[http://www.bioinformatics.org/librarian/index.php](http://www.bioinformatics.org/librarian/index.php)

Para todo aquel que investigue... recomiendo que vean el link

no lo he probado aun.

Google Translate:

Perdon not write in English. 

 It's called librarian 

 [http://www.bioinformatics.org/librarian/index.php](http://www.bioinformatics.org/librarian/index.php) 

 For anyone who investigate ... I recommend them to see the link 

 I have not tried yet.

---

### Post by vietseo on 2008-09-11
We can't miss this software :

> JabRef is an open source bibliography reference manager. The native file format used by JabRef is BibTeX, the standard LaTeX bibliography format. JabRef runs on the Java VM (version 1.5 or newer), and should work equally well on Windows [Microsoft]("http://www.vietseo.net/yahoo/cuoc-chien-yahoo-microsoft/"), Linux and Mac OS X.
Availble at this adress : 

[http://jabref.sourceforge.net/](http://jabref.sourceforge.net/)

---

### Post by garba on 2008-09-24
engauge and gnuplot

---

### Post by jotacebusta on 2008-10-17
There is also TeXmacs. It's really great, though it's not completely stable and some how hard to use.

It is a WYSYWYG document processor tha allows to obtain (and see) LaTeX quality documents. But it also can be used as an interface to R, SciLab, Octave, Maxima, and others. I really love it, even if there are still some few things I can't do.

Also, TeXmacs developers are already working on version 1.0.7, but the one in the repos is very old (1.0.6.11, I think, and there is at leart a 1.0.6.15 version...)

Does anyone know about something like Scientific Workplace? Besides TeXmacs, I know the linux version of Lyx can evaluate some expressions by using maxima. Other ideas?

---

### Post by 080729jk on 2008-10-30
&#26234;&#33021;&#21270;&#30340;&#23458;&#25143;&#31649;&#29702;&#24037;&#20855;&#12290;[**&#29627;&#29827;&#38548;&#26029;**](http://www.bjhuilehao.com/page02.htm)&#26681;&#25454;&#27599;&#20010;&#35775;&#23458;&#30340;&#19981;&#21516;&#34892;&#19994;&#65292;&#20998;&#21035;&#26631;&#27880;&#35775;&#23458;&#36523;&#20221;**&#65292;**[**&#29627;&#29827;&#38548;&#26029;**](http://www.bjhuilehao.com/page02.htm)&#32534;&#36753;&#35775;&#23458;&#20449;&#24687;&#35760;&#24405;&#22791;&#26696;&#65292;[&#29627;**&#29827;&#38548;&#26029;**](http://www.bjhuilehao.com/page02.htm)&#24050;&#22791;&#35775;&#23458;&#19979;&#27425;&#20877;&#26469;&#25552;&#20379;&#26356;&#20026;&#20307;&#36148;&#32454;&#24494;&#30340;&#26381;&#21153;&#24179;&#21488;&#31995;&#32479;&#26377;&#33258;&#21160;&#24674;&#22797;&#21151;&#33021;[**&#29627;&#29827;&#38548;&#26029;**](http://www.bjhuilehao.com/page02.htm)&#65292;&#20351;&#24471;&#22312;&#24847;&#22806;&#23445;&#26426;&#26102;&#33021;&#22815;&#22312;&#26368;&#30701;&#26102;&#38388;&#20869;&#33258;&#34892;&#24674;&#22797;&#65307;&#24182;&#19988;&#22312;&#23445;&#26426;&#26399;&#38388;**&#65292;**[**&#29627;&#29827;&#38548;&#26029;**](http://www.bjhuilehao.com/page02.htm)&#20381;&#28982;&#33021;&#22815;&#20445;&#25345;&#22312;&#32447;&#23458;&#25143;&#30340;&#36890;&#35759;&#19981;&#21463;&#20013;&#26029;&#12290;

---

### Post by neoflight on 2008-10-31
> **myle said:**
> I agree with you. Even if Kile has a better reputation, I think if you ise Gnome, it's better to use TeXmaker.

I concur.

---

### Post by neoflight on 2008-10-31
anyone installed abaqus in linux? i have the steps [CAE Journal]("http://www.caejournal.com/").

I am having some trouble getting ansys multiphysics working. if anyone got it working please write a howto there in the link above?

---

### Post by Spike the Dingo on 2008-12-03
SAGE... I'm an R geek and I just discovered SAGE. It's positively wonderful! I hope it gets in the Ubuntu repository soon! It doesn't get enough press!

[http://www.sagemath.org/index.html](http://www.sagemath.org/index.html)

I think it's going to be big!




...(R is still the best for stats)

---

### Post by windhair on 2008-12-10
> **mips said:**
> People, have a look at this:

[http://www.openchannelfoundation.org/](http://www.openchannelfoundation.org/)
[http://www.openchannelfoundation.org/cosmic/](http://www.openchannelfoundation.org/cosmic/)

Please note that the above is NOT free but could prove valuable to some people.



It is  restricted to US citizens.

---

### Post by zhangmeizhu on 2008-12-11
i found earlier that my computer is infected of svchost? Do i really need to reformat it? Coz i don't know really what to do...help!


PLS. SUPPORT MY SITE TOO! THANKS!
[www.chinitako.com](www.chinitako.com)
[www.zhangken.blogspot.com](www.zhangken.blogspot.com)
[www.illegalstudent.blogspot.com](www.illegalstudent.blogspot.com)
[www.musikandlyrix.blogspot.com](www.musikandlyrix.blogspot.com)
[www.xkiravsl.blogspot.com](www.xkiravsl.blogspot.com)
[www.ukay2x.blogspot.com](www.ukay2x.blogspot.com)

---

### Post by zhangmeizhu on 2008-12-11
i found earlier that my computer is infected of svchost? Do i really need to reformat it? Coz i don't know really what to do...help!


PLS. SUPPORT MY SITE TOO! THANKS!
[www.chinitako.com](www.chinitako.com)
[www.zhangken.blogspot.com](www.zhangken.blogspot.com)
[www.illegalstudent.blogspot.com](www.illegalstudent.blogspot.com)
[www.musikandlyrix.blogspot.com](www.musikandlyrix.blogspot.com)
[www.xkiravsl.blogspot.com](www.xkiravsl.blogspot.com)
[www.ukay2x.blogspot.com](www.ukay2x.blogspot.com)

---

### Post by zhangmeizhu on 2008-12-11
i found earlier that my computer is infected of svchost? Do i really need to reformat it? Coz i don't know really what to do...help!


PLS. SUPPORT MY SITE TOO! THANKS!
[www.chinitako.com](www.chinitako.com)
[www.zhangken.blogspot.com](www.zhangken.blogspot.com)
[www.illegalstudent.blogspot.com](www.illegalstudent.blogspot.com)
[www.musikandlyrix.blogspot.com](www.musikandlyrix.blogspot.com)
[www.xkiravsl.blogspot.com](www.xkiravsl.blogspot.com)
[www.ukay2x.blogspot.com](www.ukay2x.blogspot.com)

---

### Post by zhangmeizhu on 2008-12-11
i found earlier that my computer is infected of svchost? Do i really need to reformat it? Coz i don't know really what to do...help!


PLS. SUPPORT MY SITE TOO! THANKS!
[www.chinitako.com](www.chinitako.com)
[www.zhangken.blogspot.com](www.zhangken.blogspot.com)
[www.illegalstudent.blogspot.com](www.illegalstudent.blogspot.com)
[www.musikandlyrix.blogspot.com](www.musikandlyrix.blogspot.com)
[www.xkiravsl.blogspot.com](www.xkiravsl.blogspot.com)
[www.ukay2x.blogspot.com](www.ukay2x.blogspot.com) 

THANKS

---

### Post by Functional_Fooled on 2009-03-10
To repeat what I know a number of others have already said, R for statistics is very useful.  I taught myself how to use it while taking my graduate level statistics classes (trying out homework and redoing labs done in SAS in R to re-enforce my understanding).  I then used it for the statistical computations in my thesis and the generation of all graphs.  There may be better ways of making professional graphs or plots, but I liked having a test file of the commands I could tweak and play with until I got the look I wanted.

---

### Post by cholericfun on 2009-03-21
as a matlab person i quiet like octave,
just thought to mention that its well capable of a few things that recurrently are mentioned here: stats and graphs.
 
and if you need some specific packages theres no harm looking at the matlab file exchange for scripts that do what you need to get done.
its also a nice "front end" to gnuplot (if you have some matlab experience) - i think with all or most of the functionality of the plotting commands in matlab i.e. setting grids/color,linetypes and whatnot.


by way of plotting:
grace is a rather click-around based plotting tool,
which makes quiet good graphs

---

### Post by grinias on 2009-03-26
See also post #583 of [this]("http://ubuntuforums.org/showthread.php?t=29919&highlight=beta&page=59")...

---

### Post by parktownprawn on 2009-03-27
I just learned about [Scubuntu]("http://scubuntu.meraka.org.za/wiki/Home") who aim to develop a flavour of Ubuntu Linux for use by scientists. Looks promising.

---

### Post by grinias on 2009-03-27
> **parktownprawn said:**
> I just learned about [Scubuntu]("http://scubuntu.meraka.org.za/wiki/Home") who aim to develop a flavour of Ubuntu Linux for use by scientists. Looks promising.

thanx for this :KS

---

### Post by skotos on 2009-05-18
[http://geogebra.org](http://geogebra.org)

It is truly cross platform: GNU/Linux with Ubuntu specific package, Windows, Mac OSX and Java VM.

---

### Post by dchandan on 2009-08-15
I mostly use python for scientific progrmming. It is very powerful, has a lot of useful packages available and is very easy and quick to program. A lot of universities are switching over to python for teaching undergrads scientific programming. I would suggest getting Python 2.6 at the moment and not 3.0, because a lot of important packages have not been ported over to 3.0. 

Some useful pyhton packages/add-ons:
Numpy - A general-purpose array-processing package designed to efficiently             manipulate large multi-dimensional arrays of arbitrary records.

Scipy - Python libraries for mathematics, science, and engineering.

ScientificPython - A Python library for common tasks in scientific computing. Useful for people in atmospheric physics, oceanography, geophysics. 

Mayavi - Mayavi includes two related packages for 3-dimensionali             visualization: Mayavi which is a tool for easy and interactive             visualization of data; and TVTK which is a wrapper for the             popular, open-source, visualization library known as VTK.

HDF4 - HDF is a physical file format for storing scientific data.

Cython - A language for writing C extensions for Python, based on Pyrex,             but with more cutting edge functionality and optimizations.

PIL - Python Imaging Library provides powerful             image processing and graphics capabilities.

Chaco - Chaco is a Python plotting application toolkit that facilitates             writing plotting applications at all levels of complexity, from             simple scripts with hard-coded data to large plotting programs with             complex data interrelationships and a multitude of interactive             tools.

A good list of useful packages can be found on this page - [http://www.enthought.com/products/epdlibraries.php](http://www.enthought.com/products/epdlibraries.php) .

You should also download these:

Paraview - **ParaView** is an open-source, multi-platform data analysis and visualization application. [http://www.paraview.org/](http://www.paraview.org/)

Fenics - FEniCS is free software for automated solution of differential equations. We provide software tools for working with computational meshes, finite element variational formulations of PDEs, ODE solvers and linear algebra.  [http://www.fenics.org/wiki/FEniCS_Project](http://www.fenics.org/wiki/FEniCS_Project)

---

### Post by marako on 2009-09-03
Could I teach myself any of this?  I really like biology.... Ive been watching a bunch of ttc's on it ad just broke the spine to my new book, the ancestors tale.  Id like to contribute to science... but I lack the money to get the degree.

---

### Post by frenchn00b on 2009-09-09
QtiPlot

Description:
Data analysis and scientific plotting.
Free clone of Origin.


[http://www.kde-apps.org/content/show.php?content=14826](http://www.kde-apps.org/content/show.php?content=14826)

LabPlot

Description:
LabPlot is a KDE application for data plotting and function analysis. It support both 2D and 3D plots and tries to emulate most of the functions supported by programs like Microcal Origin or SPSS Sigmaplot.

[http://www.kde-apps.org/content/show.php?content=9881](http://www.kde-apps.org/content/show.php?content=9881)

But I cannot say, if these programmes offer the complete functionality of Origin. I used Origin at university, but never the mentionend freeware alternatives.

_________________
Kanotix-Manual (pdf):
[http://linux.kopporama.de/km_downloads.html](http://linux.kopporama.de/km_downloads.html)

Kanotix-Manual (html):
[http://linux.kopporama.de/de/Kanotix_HB.html](http://linux.kopporama.de/de/Kanotix_HB.html)
[http://linux.kopporama.de/en/kanotix_manual.html](http://linux.kopporama.de/en/kanotix_manual.html)****

---

### Post by D. Venu Gopal on 2009-09-13
Thanks for the Scubuntu link. Like edubuntu can it be available as an iso image? If it is available as an iso then it will be easier to install for novices like me.
 
I like the following to be included in Scubuntu :
 
GNU Octave
GNU Plot
Asymptote
TeX/LaTeX
R 
Kile
 
Otherwise in the edubuntu CD there is so much space available (about 300 MB). So except TeX/LaTeX all others can be accommodated on edubuntu CD.
 
Can any body give a consideration for this?

---

### Post by D. Venu Gopal on 2009-09-13
Just seen the scubuntu!! A huge repository 2.2 GB ISO image!!
 
Better it may be devided into various categories so that it can fit onto different CDs. Because I don't have a DVD drive in my computer, only CD drive. The other thing is it is easy to down load CDs than DVDs.

---

### Post by asdir on 2009-10-14
As for referencing and bibliography, you might want to replace bibus with Zotero. Though not Linux-specific, it is OSS and runs under Ubuntu. I find it much more comfortable than bibus. Most of my institute colleagues switched instantly, and they even had EndNote (which I still consider to be better than bibus).

Also, I think ESS in Emacs deserves to be mentioned in connection with R. It might not be Tinn-R, but it certainly is more helpful than just having a naked R in a terminal.

---

### Post by baniasad on 2009-11-29
Replace Windows Warez?

[B]Open Source Ubuntu!
Clo$$ed $$ource [/B]**Windows 7**


[I]**Open Source** R 
[/I][http://www.r-project.org/](http://www.r-project.org/)  
**clo$ed source** spss or excel

**open source** DownthemAll (extension of mozilla firefox)
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201) 
**clo$ed $ource** Internet download manager

**Open Source** Scrapbook (extension of mozilla firefox)
[https://addons.mozilla.org/en-US/firefox/addon/427](https://addons.mozilla.org/en-US/firefox/addon/427)
**Clo$ed $ource** meta product off line explorer
[B]
Open source[/B] Jabref Or mendeley
[http://www.mendeley.com/](http://www.mendeley.com/)
[jabref.sourceforge.net]("http://ubuntuforums.org/jabref.sourceforge.net")
** Clo$ed Source** Endnote X3

**Open source**  mid (extension of mozilla firefox)
[https://addons.mozilla.org/en-US/firefox/addon/524](https://addons.mozilla.org/en-US/firefox/addon/524)
**clo$ed $ource** Babylon

---

### Post by samden on 2009-11-29
Mendeley is closed source.

And drop all the dollar signs. Most of us are professionals and know you have to pay for stuff sometimes, it's not like money is evil or anything. Even open source developers have to be paid by someone somewhere along the line for something, or they'd starve. 

You sound like a teenager who's just discovered open source software and are temporarily enthusiastic about it being the best thing ever in the whole wide world, while everything else is brewed from the faeces of Satan. But next month you'll forget it and be on to a new fad, maybe genetic engineering or nuclear power or something. 

Teenagers.

---

### Post by bondmatt on 2009-12-21
[www.caelinux.com](www.caelinux.com)

The latest release is 64bit Ubuntu (8.04 LTS). The focus for this package is mechanical/civil engineering. I think there is essentially one person responsible for this package. There are quite a few little tools included to make it easy to use.

It does look like ubuntusci would give this a run for its money but if your an engineer I think CAELinux is a little more interesting.

---

### Post by Janneman27 on 2010-01-07
I am used to using Matlab on Windows Systems at work, but only have ubuntu systems at home. I need an alternative to matlab and have used Octave before (Windows version).

What is the most like Matlab, QtOctave or Scilab?

Any comments on usability?

---

### Post by barnex on 2010-01-11
> **Janneman27 said:**
> I am used to using Matlab on Windows Systems at work, but only have ubuntu systems at home.

Matlab does run on linux (if you have the licence, that is). Otherwise, I personally like octave.

---

### Post by bondmatt on 2010-01-22
I think Scilab is a completely different program whereas Octave and Matlab and nearly identical (I think they both have very similar programming). QtOctave or XOctave are very similar to Matlab. Octave through a plain terminal can be a bit shocking at first. The standard text editor that comes with Ubuntu has Octave highlighting capabilities built in which is very nice. I really like that text editor.
 
Best regards,
- Matt Bondy

---

### Post by Raamanaur on 2010-03-02
What about considering the package **gedit-latex-plugin **as a LaTeX editor? I didn't go through all the thread so I'm sorry if someone already commented about it, but since I didn't see it in the first post I assume that's not the case. I'm currently using this editor and I think it's a great option for Gnome users since it weights only 2MB compared to almost 200MB for Lyx and around 650MB for Kile.

---

### Post by kordenal on 2010-03-11
Hello Gurus.
Can anybody help me - how to re-calculate all Maxima's formulas in TexMacs document?

Thanx...

---

### Post by superarthur on 2010-03-11
Well, many scientists who are willing to share their software share them in source code and linux binary only.
One example is HMMER, a sequence homology search software using Hidden Markov Model
[http://hmmer.janelia.org/](http://hmmer.janelia.org/)

---

### Post by Azrael3000 on 2010-04-08
> **Raamanaur said:**
> What about considering the package **gedit-latex-plugin **as a LaTeX editor? I didn't go through all the thread so I'm sorry if someone already commented about it, but since I didn't see it in the first post I assume that's not the case. I'm currently using this editor and I think it's a great option for Gnome users since it weights only 2MB compared to almost 200MB for Lyx and around 650MB for Kile.

seconded.

Another good bib tool is JabRef. Can be found in the repos and is based on Java.

---

### Post by rajn on 2010-05-10
Python especially - its scientific packages Scipy, Numpy. There are options to integrate it with C++ or Fortran.

Even better: SAGE integrates python, and other software which also includes symbolic math alternatives.

---

### Post by manzdagratiano on 2010-05-25
> **Spike the Dingo said:**
> SAGE... I'm an R geek and I just discovered SAGE. It's positively wonderful! I hope it gets in the Ubuntu repository soon! It doesn't get enough press!

[http://www.sagemath.org/index.html](http://www.sagemath.org/index.html)

I think it's going to be big!




...(R is still the best for stats)

SAGE is indeed phenomenal!!! It contains R and Maxima, and much more... I have completely discarded Mathematica in favor of SAGE.

---

### Post by manzdagratiano on 2010-05-25
And the best deal is, aside from it being open-source, it is written in Python!!! The author, William Stein, is a Professor of Mathematics at the University of Washington. His blog:

[http://sagemath.blogspot.com/](http://sagemath.blogspot.com/)

is quite compelling - especially the history of SAGE:

[http://sagemath.blogspot.com/2009/12/mathematical-software-and-me-very.html](http://sagemath.blogspot.com/2009/12/mathematical-software-and-me-very.html)

READ it pray!

---

### Post by attila82 on 2010-07-06
- matplotlib 2D, graphs & more
[http://matplotlib.sourceforge.net/f](http://matplotlib.sourceforge.net/f)

- mendeleydesktop  -  to organize documents, papers...
[http://www.mendeley.com/](http://www.mendeley.com/)

---

### Post by tonyt3 on 2010-08-29
One of the best packages I have seen is Matlab.  It is not open source -- a proprietary version of which Octave is available as open;  available for all OS.  a huge percentage of people in the earth sciences use it.  extensible, interpreted.   [www.mathsoft.com](www.mathsoft.com)

---

### Post by zhangtudou on 2010-11-22
Is any physicist using [ROOT]("http://root.cern.ch/drupal/")?  
[http://root.cern.ch/drupal/](http://root.cern.ch/drupal/)
It is powerful on data analysing, based on C++,  gets a lot of open source classes.

sudo apt-get install root-system

---

### Post by ibsys2562 on 2010-12-05
> **towsonu2003 said:**
> I would (unfortunately) add qemu for those who have no time to learn a new program and need solution right away (thus using Windows)... again, unfortunately. 

PS. SPSS => R != GUI => qemu + keku + SPSS
Hey! None of you Ubuntu scientists would happen to be *social* scientists, would you? And if you are (or not) would you happen to know how to get the latest version of PSPP from CVS? When I do the first step described in their instructions (make -f Smake) it works for a while, then prints out a lot of commented "include" statements, and then the following:

---

### Post by kokoshmusun on 2010-12-05
I am a social scientist, but have never used PSPP.  I could use it on some tests, but normally I need a lot more options than PSPP offers at the time.  I've been thinking about switching to R, but haven't found the time.  If you're interested in learning it together, we could team up to give each other encouragement.

---

### Post by Love-computers on 2011-01-05
I use free pascal :)

---

### Post by johny28 on 2011-01-11
i use matplotlib 2D its great tools

---

### Post by mlamorey on 2011-01-13
I'm looking for a circuit / field simulator.
Very little to do with silicon or cmos more along the lines of relays and MEMS. Any thoughts / experience?

Also, I' a heavy Matlab user at work and based upon input from this forum I'm going to go with Octave rather than buying Matlab for Linux at home.

---

### Post by MrPok on 2011-03-03
**Gephi**
> *"Gephi is an interactive visualization and exploration platform for all kinds of networks and complex systems, dynamic and hierarchical graphs."*

Exploratory Data Analysis: intuition-oriented analysis by networks manipulations in real time.

Link Analysis: revealing the underlying structures of associations between objects, in particular in scale-free networks.

Social Network Analysis: easy creation of social data connectors to map community organizations and small-world networks.

Biological Network analysis: representing patterns of biological data.

Poster creation: scientific work promotion with hi-quality printable maps.

([www.gephi.org](www.gephi.org))
 


It has decent poster-size pdf output for poster presentations and such.. nice for academia.

[http://gephi.org/users/download/](http://gephi.org/users/download/)
[http://gephi.org/users/install/#linux](http://gephi.org/users/install/#linux)
(after unzipping, you can for example mv your folder to */opt/*)

---

### Post by zampes on 2011-03-09
Resources for scientists working with DNA Sequencing
During the last couple of months I've been working on acquiring software to work on different aspects of DNA sequencing, DNA sequence cleaning, Phylogenetic tree drawing, Blasting, DNA Database look-up and matching, ITS Extracting, and Statistical Analysis.

The following is a list of packages you can download via Synaptic in Ubuntu, or whatever method you use. You can also search for these packages online, in case they are not available through synaptic... and some aren't, sadly. These are all *free software*, unless otherwise indicated. I hope this saves future M.Sc. students some time and effort (God knows it took me forever to find all these tinhgs! ;) )
I'm sorry I had to include non-free software; I also hope this will show us all what there's still to be done in our community!


**_SeaView:_** Multiple Sequence Alignment editor, reads and writes various file formats (NEXUS, MSF, CLUSTAL, FASTA, PHYLIP, MASE, Newick)

**_RKWard:_** R project for Statistical Analysis, in this case with an incredibly useful graphic user interface (GUI) (uses KDE libraries, but will work fine in gnome, xfce, etc., you don't have to  switch to KDE to use it.)

**_[COLOR="Blue"]ClustalX[/COLOR]_**: For DNA alignment and drawing Phylogenetic Trees

**_[[COLOR="Blue"][COLOR="Blue"]Phylip[/COLOR][/COLOR]]("http://evolution.genetics.washington.edu/phylip.html")_**:	is a package of programs for inferring phylogenies (evolutionary trees).  also provides source code!

[B][U][URL="http://www.emerencia.org/FungalITSextractor.html"]
[COLOR="Blue"]Fungal ITS Extractor[/COLOR][/URL][/U][/B]:	An ITS1/ITS2 extractor for the fungal ITS region. Simple page with download link.
	

**_[[COLOR="Blue"]FinchTV[/COLOR]]("http://www.geospiza.com/Products/finchtv.shtml")_**:	NOT FREE SOFTWARE, although at least it is free of charge and there's a Native Linux Version! It reads Chromatogram viewer, BLAST, reverse complement sequences, etc. 	
		
**_EstimateS_**: NOT FREE SOFTWARE, windows executable ONLY. Version 8.2. DOES NOT work under WinE (no matter the version), so use version 7.5. which does run perfectly well under WinE. However, most of the things you can do with EstimateS, you can do better with R Project, which IS Free Software.

**_[COLOR="Blue"]DNA Baser[/COLOR]_**: NOT FREE SOFTWARE, windows executable ONLY. It runs very well on WinE. Sequence alignment and automatic cleaning of DNA sequence, with will save you a lot of time. DOWNSIDE: trial period is 5 hours... you read that right: 5 (five) hours...

**_[[COLOR="Blue"]Geneious[/COLOR]]("http://www.geneious.com/")_**: NOT FREE SOFTWARE, although at least it is free of charge and there's a Native Linux Version (although it is a hassle to install it, and requires the proprietary version of Java, does not support OpenJDK)! 

For a list of free software packages available for bioinformatics, see: **_[http://packages.gentoo.org/category/sci-biology?full_cat](http://packages.gentoo.org/category/sci-biology?full_cat)_**

In case you are looking for a complete suite of programs all bundled in one distro, all free software, no-hassle, check out

[[COLOR="Blue"]BioPuppy Linux[/COLOR]]("http://biopuppy.org/features.html"): [http://biopuppy.org/features.html](http://biopuppy.org/features.html)
[[COLOR="Blue"]DNALinux[/COLOR]]("http://www.dnalinux.com/"):       [http://www.dnalinux.com/](http://www.dnalinux.com/)
[[COLOR="Blue"]BioLinux[/COLOR]]("http://nebc.nerc.ac.uk/tools/bio-linux-5/bio-linux-5.0"):       [http://nebc.nerc.ac.uk/tools/bio-linux-5/bio-linux-5.0](http://nebc.nerc.ac.uk/tools/bio-linux-5/bio-linux-5.0)

---

### Post by cwarner7_11 on 2011-04-24
The [CAELinux 2010]("http://www.caelinux.com/CMS/") distro is built on Ubuntu 10.04, and includes a lot of the packages here (Scilab, Octave, R, Maxima- however, primarily focusing on FEA, including fluid dynamics, stress analysis, dynamic simulation, etc.  Very powerful.  The primary advantage of the CAELinux distro over picking up these packages independently is the fact that all of the dependencies are already worked out, and everything works out of the box...

---

### Post by cwarner7_11 on 2011-04-24
I recently did a summary of various packages available for circuit simulation- you can find it [here]("https://files.one.ubuntu.com/biRojnEQQU-X3l5TiIJhIA").  You may be interested in the Xcos package included with [Scilab]("http://www.scilab.org/products/xcos/features"), or the original [Scicos]("http://www-rocq.inria.fr/scicos/") package.

---

### Post by juancarlospaco on 2011-05-19
Hi    
&#664;&#8255;&#664;

By random browsing this forum i ended here, and read the kind of software listed,
im a Python developer that make some Chemistry related software for my LoCo and
i think that it can be useful for someone here, and want to share the GPL apps, 
the software is done via specifications of a person that teach Chemistry using Ubuntu,
i never traduced the apps because i never find someone interested, all are .DEB packed,
you can extract the .deb's and read the source, all are plain text files (with .py extension)
its on Spanish ...but its open source, and easy to traduce or use.

**[SIZE="4"]Try Hot[/SIZE]**
[[IMG]https://lh3.googleusercontent.com/_aWHwXiftflE/TXlgWErhomI/AAAAAAAAAOM/0dfuf37UcnU/tryhot.jpg[/IMG]]("http://tecnicoslinux.com.ar/livecd/tryhot_0.5_all.deb")

**[SIZE="4"]PyGAS[/SIZE]**
[[IMG]https://lh5.googleusercontent.com/_aWHwXiftflE/TXlfVbMmodI/AAAAAAAAAN8/gnWq4_nc-0c/pygas.jpg[/IMG]]("http://goo.gl/4emlU")

Im writing more apps all the time, you can search for more here: 
[https://wiki.ubuntu.com/juancarlospaco](https://wiki.ubuntu.com/juancarlospaco)

Thanks  
^&#8255;^

---

### Post by hydroxygen on 2011-06-01
Does anyone know if there is a open source equivalent of EniG Chemistry Assistant ?

---

### Post by mJayk on 2012-12-15
You neeeed  to include jabref in the bibliography section :)

---

### Post by Christian Poulsen on 2013-04-17
Hi all,

I am looking for freeware that can do the same thing as dedoose.com.
That is allow learners to make annotations from documents, videos or audio.
Can anyone give me some direction where to look?

---

### Post by patrick295767 on 2013-05-27
what about a version  based on the console ?
Efficient and reliable

[http://ncursespim.scienceontheweb.net/nframe-os.htm?p=screenshots](http://ncursespim.scienceontheweb.net/nframe-os.htm?p=screenshots)

---

### Post by mohanbylapudi on 2014-05-17
Hi, I am mohan bylapui a basic linux user. I am very enthusiastic towards the linux system level programming, So i would like to request any one of u kindly tell me the concepts i have to be very clear and suggest me any system level project.

Thanks in advance....

---

### Post by qpanas on 2014-10-27
Not exactly on topic, but strongly associated with it. I am looking for the best hardware configuration for use with scientific software for mathematics / statistics. I currently have two configurations that I take into consideration. It is described here: 
[http://ubuntuforums.org/showthread.php?t=2250111](http://ubuntuforums.org/showthread.php?t=2250111)
I have written here, because I think here will be people who are related to academic work. Sorry if I should not have.

---

### Post by Ric_Helm on 2014-10-27
Does "scientific" include electrical engineering?
I have been trying to use Multmeter, LCR, and Hand Scope software through WINE to work.

I suspect that I just do not know how to install drivers through WINE, however using search terms for multimeter or DMM only pull up threads that were quickly closed..
FYI, the Test Equipment is as follows, an Amprobe DMM via Serial to USB adaptor, A Velleman Hand Scobe also via Serial to USB adaptor, two Uni-T DMM's directly to USB.
Plus the Arduino IDE

---

