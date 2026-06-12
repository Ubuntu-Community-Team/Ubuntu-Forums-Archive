---
title: "LaTeX and epstopdf"
date: 2007-11-04
forum: Education &amp; Science
---

### Post by tonyr1988 on 2007-11-04
I'm having problems with Gutsy and latex. I'm using pdflatex, so I can't use my *.eps files (I have one generated from gnuplot). I need to convert it - I could have sworn there was a program called epstopdf installed, but I cannot find it.

I have texlive installed, and did an apt-cache search of epstopdf, but nothing came up. Did epstopdf use to be in the repos, or am I dreaming?

Also, is there somewhere else to download it? I'm having troubles finding it on the Internet to download.

Or....is there an alternative to do what I'm needing?

Thanks!

---

### Post by mzilhao on 2007-11-04
what exactly do you want to do?
do you want to put the eps file on a latex document?

---

### Post by gerdt on 2007-11-04
I am having the same problem. 
Under Feisty there was a program called epstopdf
Under Gutsy it is gone (I think)
I also need to convert eps files to pdf in order for pdflatex to process them.
Anyone knows how to install epstopdf? I can't find it in the repository.
Thanks in advance!

---

### Post by gerdt on 2007-11-04
@tonyr1988: I don't know where you create your eps files, but if you draw things with OpenOffice Draw, you can export directly to pdf.

---

### Post by HypnoticSpecter on 2007-11-04
In Gutsy epstopdf is a part of bin-pdftools, which is a part of texlive-extra-utils. So just install texlive-extra-utils.

---

### Post by gerdt on 2007-11-04
```
$ sudo apt-get install **texlive-extra-utils**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package texlive-extra-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  **texlive-base-bin dvidvi**
E: Package texlive-extra-utils has no installation candidate

``````
$ sudo apt-get install **texlive-base-bin dvidvi**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
texlive-base-bin **is already the newest version**.
dvidvi **is already the newest version**.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

``````
$ epstopdf
The program 'epstopdf' is currently not installed.  You can install it by typing:
sudo apt-get install texlive-extra-utils
bash: epstopdf: command not found

```
So somehow my system thinks epstopdf is part of texlive-extra-utils but in reality it isn't.

What is missing in my system? Does anybody know?

---

### Post by gerdt on 2007-11-04
I found a site with a script called eps2pdf

it does the same as epstopdf, but as that doesn't work on my system, eps2pdf is a nice alternative while waiting for the answer to the epstopdf-problem...

I found it through [this]("http://ubuntuforums.org/showthread.php?t=6014&highlight=epstopdf") post, though the link in that post doesn't exist anymore. This is now the correct link: [http://euridice.tue.nl/~wkager/tools.htm]("http://euridice.tue.nl/~wkager/tools.htm")

---

### Post by gerdt on 2007-11-04
> **ahmatti said:**
> You can use ps2pdf, which works also for eps figures.
the disadvantage of ps2pdf is that it converts the eps into a whole page.
what often is wanted, is to convert only a selection, i.e. to remove all empty space.
Thats where the above script comes handy

---

### Post by tonyr1988 on 2007-11-04
I was using gnuplot to make the .eps file - I'm sure you can have it set the terminal to jpeg or something else, but I really didn't want to go through and re-do all of my graphs.

Installing texlive-extra-utils worked perfectly, and epstopdf seems to be working fine.

Thanks a ton, guys!

P.S. When I typed "epstopdf" earlier (before installing texlive-extra-utils), it just said command not found - it didn't say anything about which package to install, like it does on many other applications. Do I need to do some apt command to "rebuild" the database of those things or something? Just a curiosity...

---

### Post by gerdt on 2007-11-05
@tonyr1988: So you just installed texlive-extra-utils without any problems? apt didn't tell you to install texlive-base-bin dvidvi instead? Can I see your sources.list? Perhaps I am using the wrong ones?

---

### Post by tonyr1988 on 2007-11-05
> **gerdt said:**
> @tonyr1988: So you just installed texlive-extra-utils without any problems? apt didn't tell you to install texlive-base-bin dvidvi instead? Can I see your sources.list? Perhaps I am using the wrong ones?
Yeah, I had no problems whatsoever. It installed just fine, and everything began working immediately. Here's my apt sources.list. I believe it's just the default repos - I haven't touched them in a long time.:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## OOoLatex
# deb [http://www.fyma.ucl.ac.be/ubuntu](http://www.fyma.ucl.ac.be/ubuntu) feisty contrib

---

### Post by LaserJock on 2007-11-08
> **tonyr1988 said:**
> Yeah, I had no problems whatsoever. It installed just fine, and everything began working immediately. Here's my apt sources.list. I believe it's just the default repos - I haven't touched them in a long time.:

I actually just did a fresh Gutsy install last night and since I'm working on my dissertation in pdflatex I just happened to need epstopdf today :-)

I just installed texlive-extra-utils and I now have epstopdf. gerdt, what Ubuntu release and package versions are you using?

-LaserJock

---

### Post by gerdt on 2007-11-12
Sorry I didn't reply earlier, but I already solved it. 
I don't know why, but I had a source in my sources.list commented out. It turned out that was the source I needed for installing texlive-extra-utils.
After uncommenting it I could install it without a problem.
Thank you tonyr1988 for letting me compare your list with mine.

---

### Post by tonyr1988 on 2007-11-14
It's no problem - glad it works for you!

---

### Post by EmmetCaulfield on 2007-11-21
Just had the same problem and found the answer here.

Ludicrous that one should have to install support for Mongolian and a dozen other fringe languages to use epstopdf, though. If you use pdflatex, you likely use epstopdf, so it should be in with that rather than a whole slew of little-used stuff.

---

### Post by KiwiDalang on 2007-11-26
I have what looked like a similar problem, but I seem to have epstopdf and still have the problem.

I am using the Lyx 1.5.1 that shipped with Gutsy
That didn't automatically kick up imagemagick as required, and I eventually figured out that that was the problem in the on-screen display.
But the dvi produced has no graphics, just boxes where they should be.

Any ideas? I am fairly desperate by now, as I have a dissertation written in Lyx that I can't print out any more - it worked fine in the 1.4.? that was included in feisty. I'm at the point of thinking I might have to reinstall Feisty :(

---

### Post by KiwiDalang on 2007-11-26
It seems like latex is not generating the graphics for the dvi. I don't know whether there are other dependencies needed to do that.

pdflatex does work though, so I am using that.

---

### Post by gerdt on 2007-11-27
This seems like a latex problem, not an ubuntu problem. you say you generate a dvi. this means that you are using latex instead of pdflatex. Try to google "latex graphics dvi pdf" and a lot of usefull answers appear.

For dvi's (the command latex), including pdf's is useless. For pdf's (the command pdflatex) including jpg's is useless. latex and pdflatex respectively, only understand certain graphic extensions. dvi understands among others eps and jpg. pdflatex understands among others pdf

So, if you want to be absolutely sure your picture is included in you thesis, remove the extension of your picture within the \begin{figure}, so that only the actual name of the picture is included. Then, make several copies of your picture, each with a different extension. Place them in the same directory so that latex or pdflatex can choose his favorite extension. Make an eps, pdf, jpg, png for example.

---

### Post by baye on 2008-01-15
Thank you all guys!

I had the same problem since I migrated from fiesty to gusty (....a couple of months). I just can compile now with pdflatex since installing texlive-extra-utils
.\\:D/.

---

### Post by havok1977 on 2008-09-02
Thanks to the info in this post i can now convert eps to pdf on my Hardy machine; but when i try to actually include the newly converted image in my latex file i get the following error:

```

! Undefined control sequence.
l.43 \includegraphics
                     {tutte.pdf}
?

```

The file is present in the current working directory, so why the hell doesnt latex know what to do?

---

### Post by hugmenot on 2008-09-02
Did you load the graphicx package with \usepackage{graphicx} ?

---

### Post by peterpall on 2008-11-22
It doesn't really seems like this has happened in this case, but a common thing to go wrong is that 
[LIST]
[*]LaTeX doesn't support pdf images. It only, and I mean *only* supports eps
[*]pdfLaTeX supports everything *except* eps.
[/LIST]
Both programs know which file endings they can use and which not, so it sometimes comes handy to leave out the ".pdf" from the filename given in the \includegraphics command: Both programs will add the ending appropriate for them automatically which makes the same file usable for LaTeX and pdfLaTeX at the same time.

The only other thing that happens quite often is  that if a tex file inside a subdir is \include'd --- LaTeX still uses the directory it was started in as curdir, so for pointing to other places than the one LaTeX was started at a relative path has to be given.

---

### Post by Leporello on 2008-12-04
I am experiencing the same problem as KiwiDalang. The command "latex" produces an output with a box where the graphic should be, but no graphic. I made sure to include an eps version of the graphic in the same directory as the tex file. I also have a pdf version of the graphic in the directory, and pdflatex works just fine. I suppose I can just use pdflatex, but I'd like to understand why this is happening.

---

### Post by Stefan_K on 2008-12-31
Hi Leporello,

make sure that there's no option draft set for the document class or the graphicx package. In that case just a box would appear instead of the actual image. On the other side pdflatex should show similar behavior then.

Stefan

---

### Post by Ng Oon-Ee on 2009-01-23
Ah, thanks so much for the help here. I've gotten pdftricks working thanks to this, couldn't figure out where to get epstopdf at all when I was tracking down my log errors.

---

### Post by dfmalh on 2009-10-25
Hi, you can install "epstopdf" by doing the following:

> sudo apt-get install texlive-extra-utils


epstopdf is included inside this package :-)

So to convert e.g. image.eps --> image.pdf, simply do:

> epstopdf image :guitar:

I have question though...

Does anybody know the command to convert multiple .eps files to .pdf? I have more than 80 images to convert...

Thanks for any help.

---

### Post by dfmalh on 2009-10-26
This works from a terminal:

> find -depth -name '*.eps' -execdir epstopdf {} \;

Hope this will help someone else :P
Cheers

---

### Post by dfmalh on 2009-10-26
Sorry, I have to correct the code...

You may leave the -depth out.

> find -name '*.eps' -execdir epstopdf {} \;

---

### Post by svalbard on 2010-05-27
> **dfmalh said:**
> This works from a terminal:



Hope this will help someone else :P
Cheers
It most certainly has :D I'm trying to reconfigure the gEdit LaTeX Plugin to create pdfs without rubber (as it doesn't seem to function correctly for me) and your code snippet has saved me quite a bit of hassle!

---

### Post by I_K on 2012-01-24
Hello everyone.

I've got the same problem: my eps to pdf doesn't work on the fly. 

I installed ubuntu libraries containing epspdfconversion using ubuntu software centre (because I didn't understand how to download epstopdf package from CTAN _[http://www.ctan.org/pkg/epstopdf](http://www.ctan.org/pkg/epstopdf)_) and started trying.

text.tex
```

\documentclass[a4paper,12pt]{article}
\usepackage{epspdfconversion}
\usepackage{graphicx}

\begin{document}
\includegraphics[width=0.5\textwidth]{test.eps}
\end{document}
```I execute it:
```

pdflatex -interaction=nonstopmode -shell-escape test.tex

```And get the output:
```

This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 \write18 enabled.
entering extended mode
(./test.tex
LaTeX2e <2009/09/24>
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo))
(/usr/share/texmf-texlive/tex/latex/epspdfconversion/epspdfconversion.sty
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/pdftex-def/pdftex.def))
(/usr/share/texmf-texlive/tex/latex/oberdiek/epstopdf-base.sty
(/usr/share/texmf-texlive/tex/generic/oberdiek/infwarerr.sty)
(/usr/share/texmf-texlive/tex/latex/oberdiek/grfext.sty)
(/usr/share/texmf-texlive/tex/latex/oberdiek/kvoptions.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/generic/oberdiek/kvsetkeys.sty
(/usr/share/texmf-texlive/tex/generic/oberdiek/etexcmds.sty)))
(/usr/share/texmf-texlive/tex/generic/oberdiek/pdftexcmds.sty
(/usr/share/texmf-texlive/tex/generic/oberdiek/ifluatex.sty)
(/usr/share/texmf-texlive/tex/generic/oberdiek/ltxcmds.sty))
(/usr/share/texmf-texlive/tex/latex/latexconfig/epstopdf-sys.cfg))

epspdfconversion info: 
epspdfconversion.sty is using epstopdf.sty with the following setup:
    update=true,
    verbose=true,
    prefersuffix=true,
    suffix=-epspdf-to,
    outdir=,
    append,
    enable
epspdf is used like this:
    epspdf <file> 

) (/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty) (./test.aux)
(/usr/share/texmf/tex/context/base/supp-pdf.mkii
[Loading MPS to PDF converter (version 2006.09.02).]
)/usr/bin/epspdf: 3: /usr/share/texmf-texlive/scripts/epspdf/epspdf.rb: Permission denied


! Package pdftex.def Error: File `test-epspdf-to.pdf' not found.

See the pdftex.def package documentation for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.6 ...raphics[width=0.5\textwidth]{test.eps}
                                                  
[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] (./test.aux) )
(see the transcript file for additional information)</usr/share/texmf-texlive/f
onts/type1/public/amsfonts/cm/cmr12.pfb></usr/share/texmf-texlive/fonts/type1/p
ublic/amsfonts/cm/cmtt12.pfb>
Output written on test.pdf (1 page, 13577 bytes).
Transcript written on test.log.

```So, I give rights for execute to group and others for everything pdflatex asks for and get this:
```

This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 \write18 enabled.
entering extended mode
(./test.tex
LaTeX2e <2009/09/24>
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo))
(/usr/share/texmf-texlive/tex/latex/epspdfconversion/epspdfconversion.sty
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/pdftex-def/pdftex.def))
(/usr/share/texmf-texlive/tex/latex/oberdiek/epstopdf-base.sty
(/usr/share/texmf-texlive/tex/generic/oberdiek/infwarerr.sty)
(/usr/share/texmf-texlive/tex/latex/oberdiek/grfext.sty)
(/usr/share/texmf-texlive/tex/latex/oberdiek/kvoptions.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/generic/oberdiek/kvsetkeys.sty
(/usr/share/texmf-texlive/tex/generic/oberdiek/etexcmds.sty)))
(/usr/share/texmf-texlive/tex/generic/oberdiek/pdftexcmds.sty
(/usr/share/texmf-texlive/tex/generic/oberdiek/ifluatex.sty)
(/usr/share/texmf-texlive/tex/generic/oberdiek/ltxcmds.sty))
(/usr/share/texmf-texlive/tex/latex/latexconfig/epstopdf-sys.cfg))

epspdfconversion info: 
epspdfconversion.sty is using epstopdf.sty with the following setup:
    update=true,
    verbose=true,
    prefersuffix=true,
    suffix=-epspdf-to,
    outdir=,
    append,
    enable
epspdf is used like this:
    epspdf <file> 

) (/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty) (./test.aux)
(/usr/share/texmf/tex/context/base/supp-pdf.mkii
[Loading MPS to PDF converter (version 2006.09.02).]
)/bin/sh: Can't open /usr/bin/epspdf


! Package pdftex.def Error: File `test-epspdf-to.pdf' not found.

See the pdftex.def package documentation for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.6 ...raphics[width=0.5\textwidth]{test.eps}
                                                  
[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}] (./test.aux) )
(see the transcript file for additional information)</usr/share/texmf-texlive/f
onts/type1/public/amsfonts/cm/cmr12.pfb></usr/share/texmf-texlive/fonts/type1/p
ublic/amsfonts/cm/cmtt12.pfb>
Output written on test.pdf (1 page, 13577 bytes).
Transcript written on test.log.

```I found on one forum that it might be because the code is written for bash shell, not sh shell. And there are some hints how to fix it, but I am afraid to follow instructions I don't understand at all, because they might be not applicable to my case.

Does anyone have any idea how to fix the problem?

Thanks in advance!

---

