---
title: "[SOLVED] LaTeX problems in dapper?"
date: 2006-05-20
forum: Education &amp; Science
---

### Post by tjansson on 2006-05-20
I installed the kile LaTeX editor, which in return installed all the dependencies. But somehow there is LaTeX package missing. Namly srcltx.sty, which ought to be included in the kdvi ubuntu package according to [URL="http://packages.ubuntulinux.org/cgi-bin/search_contents.pl?searchmode=filelist&word=kdvi&version=breezy&arch=amd64"]

Another problems is that doesn't seem to reconize danish as the language in bable:
```

[LaTeX] essay.tex => essay.dvi (latex)
/usr/share/texmf-tetex/tex/generic/babel/danish.ldf:0: No hyphenation patterns were loaded for(babel) the language `Danish'(babel) I will use the patterns loaded for \language=0 instead.

```
which should work on other machines. 

Is there some extra tetex packages which include srcltx.sty or should I really install from the web by hand?

---

### Post by kleeman on 2006-05-20
Hmm I installed kdvi and I have that style file in

/usr/share/doc/kde/HTML/en/kdvi

What exactly is the issue?
I note that your package search was with breezy and amd64 but I thought you were using dapper.....

---

### Post by tkjacobsen on 2006-05-20
try to install the tetex-extra package. It is not installed with kile

---

### Post by tjansson on 2006-05-20
[QUOTE=tkjacobsen]try to install the tetex-extra package. It is not installed with kile[/QUOTE]
Unfortunately it already did:
```

root@newton:/home/tjansson# aptitude install kile
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  kdvi kviewshell perl-tk tetex-base tetex-bin tetex-doc tetex-extra tex-common
The following NEW packages will be installed:
  kdvi kile kviewshell perl-tk tetex-base tetex-bin tetex-doc tetex-extra tex-commo

```

---

### Post by tjansson on 2006-05-20
[QUOTE=kleeman]Hmm I installed kdvi and I have that style file in

/usr/share/doc/kde/HTML/en/kdvi

What exactly is the issue?
I note that your package search was with breezy and amd64 but I thought you were using dapper.....[/QUOTE]
You right - the package is there
```

root@newton:/usr/share/doc/kde/HTML/en/kdvi# ls
aboutkde.ps.gz  index.cache.bz2  KDVI-features.dvi.gz  kdvi-search.el        optionrequester2.png  srctex.sty
common          index.docbook    KDVI-features.tex.gz  optionrequester1.png  srcltx.sty

```
but somehow kile does not register it. When I do system check in kile it report it missing.

---

### Post by Spie on 2006-05-20
The srcltx.sty is not in the texhash update path. Everytime you add a style package to latex you should run texhash. So /usr/share/doc/kde/HTML/en/kdvi won't be checked when you run texhash. Normally, texhash is ran automatically after an apt-get install latex-package. So either put that path in the texhash update path (Add something like this:
```
declare -x TEXINPUTS=.:$/usr/share/doc/kde/HTML/en/kdvi:
```to your .bashrc) or move the srcltx.sty to a path which is updated with texhash (i.e. /usr/share/texmf-tetex/tex/latex).
After this run:
```
sudo texhash
```
And when you run LaTeX now it should be OK.

I think you can also run:
```
sudo texhash /usr/share/doc/kde/HTML/en/kdvi
```

I hope this will work for you.

Instead of running Kile, I suggest Texmaker. Not from the repositories but [download]("http://www.xm1math.net/texmaker/") the package without qt-libraries.

---

### Post by Spie on 2006-05-20
I tried to load the danish language package and on my system it just works.

After googling a while I found that the problem for some people was solved after a simple:
```
dpkg-reconfigure tetex-bin
```

Good luck with everything.

---

### Post by mannheim on 2006-05-20
I beleive the reason it is not included in the standard distribution is that srcltx.sty is not needed anymore with modern tex systems such as tetex 3.0 in dapper.

The purpose of stcltx.sty is to insert "source specials" in the dvi file, in order to allow a dvi view (such as xdvi or kdvi) to do an "inverse search" -- getting a text editor to open the source file at the point corresponding to a known point in the dvi file.

With recent versions of tex, you can get (la)**tex itself** to insert source specials, using a command-line switch:

```
latex -src-specials MyGreatWork.tex
```

Do "tex -help" for details.

---

### Post by tjansson on 2006-05-21
Spie and Mannheim:
Thanks for the advice. I just seems strange that the packages isn't installed as a dependency, when the Kile latex editor wants it. It was installed by default in Mandriva. So I guess I'll just install it by hand then. But thanks for the help :D

As to the babel and danish language support, then after running the  "dpkg-reconfigure tetex-bin" command as root it didn't change anything. Maybe it is because that the language of the installation is english and I only use Danish in Latex?

---

### Post by Spie on 2006-05-21
I don't know what you mean by "when the Kile latex editor wants it". Can't you just comment it in your LaTeX source file? Like Mannheim, I don't see the use for it. Kile is just an editor for LaTeX, it doesn't want anything unless you specify it in your source.

As for the Danish grammar, Danish is just present in /usr/share/texmf-tetex/tex/generic/babel/. I can use it but I am sure I never will ;) 
Did you use ```
\usepackage[danish]{babel}
``` in your preamble?

---

### Post by nickle on 2006-05-21
[quote=Spie] move the srcltx.sty to a path which is updated with texhash (i.e. /usr/share/texmf-tetex/tex/latex).
After this run:
```
sudo texhash
``` And when you run LaTeX now it should be OK.
[/quote] 
This worked for me...  Tx

---

### Post by tjansson on 2006-05-22
[QUOTE=Spie]I don't know what you mean by "when the Kile latex editor wants it". Can't you just comment it in your LaTeX source file? Like Mannheim, I don't see the use for it. Kile is just an editor for LaTeX, it doesn't want anything unless you specify it in your source.
[/QUOTE]

When I work paper in physics, which i'm am studying, there is alot of formulas and mathematics in the things I write in latex. Sometimes it can be difficult to se where in the .tex document the error resides when looking at .dvi file. I my case it is very usefull eventhough you don't see the for it. 

Thanks for pointing out that kile is an editor. I was however aware that it is only program and does not "want" things. In the program there is a option called "system check" which does check is the needed requirements for kile is present. See this picture [http://www.tjansson.dk/phpAlbum/billeder/examples/kile-srcltx.sty.jpg](http://www.tjansson.dk/phpAlbum/billeder/examples/kile-srcltx.sty.jpg)

The reason for this thread was that I could understand why ubuntus tetex packages didn't seem to include srcltx.sty in a way that made kile aware of the latex package. This was default in mandriva - so I was curios. 

As for the babel part i did included the same way you did.

---

### Post by Spie on 2006-05-24
I see you're using KDE so no need to use texmaker (like I said in an earlier post). Kile is nice! But slow if using gnome and I don't want to install all those extra kde-packages.

Nevertheless, after installing srcltx I think it is a nice tool, but with recent LaTeX versions you don't need srcltx, like Mannheim said. But if you're using Kile: 
"The LaTeX srcltx package must be loaded before forward and inverse searches will work in Kile. This package can be found on CTAN in the macros/latex/contrib/srcltx directory. In addition, TEX input files must contain the line \usepackage[active]{srcltx} and the Kile embedded viewer, Kdvi, must have an option set: Settings -> DVI Options -> DVI Specials -> Shell Command -> kile %f --line %l." ([Source]("http://www.ces.clemson.edu/linux/latex.shtml"))

And I found this (informative page with nice links):
"Producing TeX files for inverse search
There are essentially two ways to produce DVI files which contain inverse search information: you can either use a TeX/LaTeX binary which generates and includes the necessary information automatically, or you can include an extra package which is written in TeX/LaTeX.
A TeX binary which generates and includes the necessary information automatically is certainly the preferred method of including inverse search information. If you use version 2 or greater of the TeTeX TeX distribution, you can use the 'src-specials' command line option of the tex or latex command, as follows.
```
tex --src-specials myfile.tex
```
or
```
latex --src-specials myfile.tex
```
If you do not have a TeX binary which includes inverse search information natively, copy the files srcltx.sty and srctex.sty to the folder where your TeX file resides (you can do that by pressing the Shift key and left mouse button while the mouse pointer is on a hyperlink.) If you use LaTeX, add the line
```
\usepackage[active]{srcltx}
```
to the preamble of your LaTeX file. If you use plain TeX, the line
```
\include{srctex}
```
will do the trick." ([source]("http://docs.kde.org/stable/en/kdegraphics/kdvi/inverse-search.html"))

You solved the babel problem already?
Tried a
```
sudo texhash
```
like Nickle?

---

### Post by escape on 2006-05-24
Sorry for slight derail, but you might also consider lyx-qt, and qtconfig to make it look good. I have yet to have any problems iwth lyx-qt on Breezy or Dapper; works fine using Gnome as well as KDE.

---

### Post by cantormath on 2007-03-25
> **nickle said:**
> This worked for me...  Tx

This definitely fixed the problem.

first download srcltx.ins and .dtx to a folder and 
```
tex srcltx.ins
```

then move the srcltx.sty file to 
/usr/share/texmf-tetex/tex/latex
```
sudo cp srcltx.sty /usr/share/texmf-tetex/tex/latex

```

run texhash
```
sudo texhash
```

then restart kile, should be totally fixed when you run the system check in kile.

---

### Post by gstt on 2007-04-18
I am trying to configure inverse search with Kile in Ubuntu. I have googled the forum and found that the old tex system needs srcltx.sty but for the newer one it only to specify 
latex -src-specials %filename

So this might be a more convenient way to configure than copying srcltx.sty to /usr/share/texmf-tetex/tex/latex/

0) Use Synaptic Package to install kile and kdvi

1) In Kile, choose Settings-> Configure Kile -> Build -> Latex -> General 
In Options, change it to :
--src-specials -interaction=nonstopmode '%source'

2) In Kile, choose Settings-> Configure Kile -> Build -> Latex -> ViewDVI
In Advanced, choose  Run Embedded in Kile for Type.  In General it should display "kviewerpart" for Library, "KViewPart" for Library Class, "dvi" for Options

3) In Kdvi, choose Settings-> Configure Kile -> DVI Specials
Choose Kile for Editor, kile %f --line %l for Shell Command

After this, I am able to compile dvi file and use middle button to do inverse search in Kdvi. And in Kile you can do Forward search.

---

