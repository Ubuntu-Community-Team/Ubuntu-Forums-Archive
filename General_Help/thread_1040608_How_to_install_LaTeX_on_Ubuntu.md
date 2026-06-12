---
title: "How to install LaTeX on Ubuntu?"
date: 2009-01-15
forum: General Help
---

### Post by FreakyBug on 2009-01-15
I am using Ubuntu 804, and I followed the following link to install texmaker and the suggested packages:
####################################################
[http://hafizimtiaz.blogspot.com/2008/05/installing-latex-on-ubuntu-804.html](http://hafizimtiaz.blogspot.com/2008/05/installing-latex-on-ubuntu-804.html)

In Windows, usually we use WinEdt as front end LaTeX editor and Texlive or
Miktex as compiler. Texlive is available through Ubuntu repository. But
Miktex is not so easily installable in Ubuntu. You have to compile it from
scratch after downloading the source from SourceForge.net.

The replacement for WinEdt in Ubuntu might be Kile or Texmaker. Kile is a
KDE native applicaton, though you can install it on Ubuntu using Synaptic.
But you have to install some KDE libraries which you might not like!

So, I think Texmaker is the best choice. Though it is available through
Synaptic, it does not install Texlive as its dependencies [ I was very
surprised to learn that ].

Anyway, there are solutions to this problem :-)

Just select these packages manually after selecting Texmaker on Synaptic and
confirming additional packages :

tex-common
texlive-base
texlive-base-bin
texlive-common
texlive-doc-base
texlive-latex-base

After Synaptic downloads and installs the packages, you can edit and compile
LaTeX documents.

There is another problem involving Texmaker. It configures 'xpdf' as its
default PDF viewer. As Ubuntu 8.04 does not have 'xpdf', you have to set '
evince' as the default PDF viewer. To do so :

1. Go to the OPTIONS menu in Texmaker
2. Select CONFIGURE TEXMAKER
3. On the COMMANDS tab, find 'Pdf viewer' text field
4. Replace 'xpdf' with 'evince' keeping other texts on this field intact.

Now, you are done. You can view PDF by selecting VIEW PDF from TOOLS menu
after compiling the document usinf PDFLatex.
###########################################################################

After that, I used apt-get to install texlive and all its dependencies.

Now I am compiling a latex sample from an academic conference. Initially it suggested the missing of stmaryrd.sty and module.sty. However, after I downloaded and placed these two files in the directory of the tex file, texmaker still suggested the following errors: 

************** SUMMARY ************** :
line 64 -> ! LaTeX Error: *** NFSS release 1 command \define@mathgroup found
*** Recovery not possible. Use \DeclareSymbolFont. \define@mathgroup
line 64 -> ! I can't find file `.'. \define@mathgroup
line 64 -> ! Emergency stop. \define@mathgroup
************** LOG FILE *************** :

Anyone has any idea on how to fix this problem? I guess I was not configuring LaTeX compiling environment properly.

---

### Post by albinootje on 2009-01-15
> **FreakyBug said:**
> 
************** SUMMARY ************** :
line 64 -> ! LaTeX Error: *** NFSS release 1 command \define@mathgroup found
*** Recovery not possible. Use \DeclareSymbolFont. \define@mathgroup
line 64 -> ! I can't find file `.'. \define@mathgroup
line 64 -> ! Emergency stop. \define@mathgroup
************** LOG FILE *************** :

Anyone has any idea on how to fix this problem? I guess I was not configuring LaTeX compiling environment properly.
I don't know what to do about those errors, but there's an alternative to try :
[http://kile.sourceforge.net/screenshots.php](http://kile.sourceforge.net/screenshots.php)
It's in the Ubuntu repositories as "kile".
With that you could check and see whether it also gives similar problems.

---

### Post by heindsight on 2009-01-15
> **FreakyBug said:**
> Now I am compiling a latex sample from an academic conference. Initially it suggested the missing of stmaryrd.sty and module.sty. However, after I downloaded and placed these two files in the directory of the tex file, texmaker still suggested the following errors: 

************** SUMMARY ************** :
line 64 -> ! LaTeX Error: *** NFSS release 1 command \define@mathgroup found
*** Recovery not possible. Use \DeclareSymbolFont. \define@mathgroup
line 64 -> ! I can't find file `.'. \define@mathgroup
line 64 -> ! Emergency stop. \define@mathgroup
************** LOG FILE *************** :

Anyone has any idea on how to fix this problem? I guess I was not configuring LaTeX compiling environment properly.

What happens if you open a terminal, cd to the directory containing your tex file and do:
```
pdflatex file.tex
```

---

### Post by golem1989 on 2009-04-14
> **heindsight said:**
> What happens if you open a terminal, cd to the directory containing your tex file and do:
```
pdflatex file.tex
```

i got a problem with this stuff too...

when i use pdflatex file.tex, it says:

```
patrick@golem:~/Desktop$ pdflatex test.tex
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./test.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, croatian, ukrainian, russian, bulgarian, czech, slovak, danish, dut
ch, finnish, basque, french, german, ngerman, ibycus, greek, monogreek, ancient
greek, hungarian, italian, latin, mongolian, norsk, icelandic, interlingua, tur
kish, coptic, romanian, welsh, serbian, slovenian, estonian, esperanto, upperso
rbian, indonesian, polish, portuguese, spanish, catalan, galician, swedish, loa
ded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo))

! LaTeX Error: File `Amsmath.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)
```

and i dont know how to add all this .sty's ;O
isnt anything working just with packages? i dont wonna configure everything on my own :/

EDIT: SOLVED - i'm ok now... but it's quite late and i got a lot of work to do now ;>
installing latex took longer than i thought...

---

### Post by Miche on 2009-08-26
Hi Golem, 

Could you please let me know how you solved the problem? 
I'm migrating from Win to Ubuntu, Miktex to Texmaker (so far the best I found?, not so exciting by the way) but I find hard to understand where to put .sty files. 
Is there anyway (as in Miktex) for the program to automatically install the missing packages?
Any help would be really appreciated. 

- I found the solution, I just added the file into the directory where I have the .tex file. But still, does Texmaker can install by itself missing packages?

Thanks,
M

---

### Post by dmonkey on 2009-08-26
As far as I know, Texmaker (and probably all other Linux tex IDEs) will not automatically install required packages for you. Normally, if one browses the repositories, you will see that the common TeX packages (like TeXLive) are split into many sub-packages, each of which have different TeX/LaTeX packages inside. If you want a general set of extended math packages, you should just install the package texlive-math-extra. You can also view which packages are install by viewing the documentation for each package:

$ sudo aptitude show texlive-math-extra

Package: texlive-math-extra
New: yes
State: installed
Automatically installed: no
Version: 2007.dfsg.8-1ubuntu1
Priority: optional
Section: tex
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5222k
Depends: texlive-fonts-recommended (>= 2007-11), texlive-common (>= 2007),
         texlive-latex-base (>= 2007-11)
Replaces: tetex-bin (< 2007), texlive-latex-extra (<= 2005-2)
Description: TeX Live: Advanced math typesetting
 Extra math 
 
 This package includes the following CTAN packages: 
 12many -- 12many, generalizing mathematical index sets
 amstex -- American Mathematical Society plain TeX macros.
 breqn -- Automatic line breaking of displayed equations.
 ccfonts -- Support for Concrete text and math fonts in LaTeX.
 commath -- Mathematics support.
 concmath -- Concrete Math fonts.
 concrete -- Concrete Roman fonts.
 eqnarray -- More generalised equation arrays with numbering.
 extarrows -- Extra Arrows beyond those provided in AMS math
 extpfeil -- The extpfeil package.
 faktor -- The faktor package.
 hvmath -- Support for using the Micropress HV-Math fonts (Helvetica Maths).
 mathcomp -- No caption.
 mh -- The MH bundle
 mhequ -- Multicolumn equations, tags, labels, sub-numbering.
 nath -- Natural mathematics notation.
 stmaryrd -- St Mary Road symbols for functional programming.
 tensor -- Typeset tensors.
 tmmath -- Support for using the Micropress TM-Math fonts.
 venn -- Creating Venn diagrams with MetaPost.
 xfrac -- Split-level fractions in latex2e*.
 yhmath -- Extended maths fonts for LaTeX.
 bin-amstex -- American Mathematical Society plain TeX macros.
Homepage: [http://www.tug.org/texlive](http://www.tug.org/texlive)

---

One option is tu just install everything, that way you will have almost all of the packages you will ever need for compiling LaTeX documents. Another option is to manually install the .sty files yourself, which is much easier than it sounds.

Imagine you have a new package called cool.sty. Place the file in the 'TeX tree', which can normally be found at

/usr/local/share/texmf/tex/latex

This destination might not exist--if not, you can create it:

mkdir -p /usr/local/share/texmf/tex/latex

Now, place cool.sty in this folder, preferably in its own subfolder:

/usr/local/share/texmf/tex/latex/cool/cool.sty

Now you have to let your TeX installation know that you have installed something new. This is accomplished by running either

sudo texhash

or

sude mktexlsr

You should now be able to include the package in your latex file as normal without errors:

\usepackage{cool}

---

### Post by Miche on 2009-08-26
Thanks a lot Dmonkey, yor post was enlightening. It was simply what I was looking for and now it works.
More than Maths I'm "tweaking" bibliographies packages. 
Best,
Michele

---

