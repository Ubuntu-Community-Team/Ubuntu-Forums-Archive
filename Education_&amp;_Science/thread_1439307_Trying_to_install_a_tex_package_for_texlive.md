---
title: "Trying to install a tex package for texlive"
date: 2010-03-26
forum: Education &amp; Science
---

### Post by SnickerSnack on 2010-03-26
Hi all,

EDIT: Almost forgot: Ubuntu 9.10, Texlive 2007.dfsg.2-4ubuntu1.
/EDIT

I'm trying to install the package mathabx (I need/want \bigboxplus).  Of course, I have the package downloaded, but I'm having trouble getting texlive to see it.

First I followed the README:

> Suggested TDS location for all ``.mf'' files:
---------------------------------------------
$TEXMF/fonts/source/public/mathabx

Brief description of the (La)TeX files
--------------------------------------

mathabx.tex: ``plain TeX'' input file which defines the 3 families
matha (5,7,10), mathb (5,7,10) and mathx (10,10,10) then read
mathabx.dcl;

mathabx.sty: LaTeX input file which defines the 3 families matha,
mathb and mathx according to LaTeX fonts selection scheme, then read
mathabx.dcl;

mathabx.dcl: declaration of every new or conpound symbol.

Suggested TDS location: $TEXMF/tex/generic/misc/

Neither of these seem to be the correct location.

I then tried to put the dcl and sty files where others seemed to be:

/usr/share/texmf-texlive/tex/generic/misc/

EDIT2: I also have the packages here:
/usr/share/texmf-texlive/tex/latex/mathabx
/EDIT2

This didn't seem to be recognizable to texlive either.  So, the first problem is that mathabx isn't detected automatically.

However, as you may know, when the package isn't found, latex prompts for the file location:

> zsharon@Weierstrass:~/UTSA/Algebra II/latex files$ latex sandbox2.tex ; dvipdf sandbox2.dvi ; evince sandbox2.pdf 
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./sandbox2.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, arabic, farsi, croatian, ukrainian, russian, bulgarian, czech, slov
ak, danish, dutch, finnish, basque, french, german, ngerman, ibycus, greek, mon
ogreek, ancientgreek, hungarian, italian, latin, mongolian, norsk, icelandic, i
nterlingua, turkish, coptic, romanian, welsh, serbian, slovenian, estonian, esp
eranto, uppersorbian, indonesian, polish, portuguese, spanish, catalan, galicia
n, swedish, ukenglish, pinyin, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size11.clo))
(/usr/share/texmf-texlive/tex/latex/amsfonts/amssymb.sty
(/usr/share/texmf-texlive/tex/latex/amsfonts/amsfonts.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty))
(/usr/share/texmf-texlive/tex/latex/amscls/amsthm.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/graphics/dvips.def)))
(/usr/share/texmf-texlive/tex/latex/geometry/geometry.sty
(/usr/share/texmf-texlive/tex/xelatex/xetexconfig/geometry.cfg))
(/usr/share/texmf-texlive/tex/latex/fancyhdr/fancyhdr.sty)
(/usr/share/texmf-texlive/tex/latex/lastpage/lastpage.sty)
(/usr/share/texmf-texlive/tex/latex/jknapltx/mathrsfs.sty)

! LaTeX Error: File `mathabx.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name: 

It does this for the sty and dcl files:

> ! LaTeX Error: File `mathabx.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name: /usr/share/texmf-texlive/tex/generic/misc/mathabx.sty
(/usr/share/texmf-texlive/tex/generic/misc/mathabx.sty
! I can't find file `mathabx.dcl'.
l.74 \input mathabx.dcl

Please type another input file name: /usr/share/texmf-texlive/tex/generic/misc/mathabx.dcl
(/usr/share/texmf-texlive/tex/generic/misc/mathabx.dcl)) (./sandbox2.aux)
(/usr/share/texmf-texlive/tex/latex/amsfonts/umsa.fd)
(/usr/share/texmf-texlive/tex/latex/amsfonts/umsb.fd)
(/usr/share/texmf-texlive/tex/latex/jknapltx/ursfs.fd)kpathsea: Running mktextfm matha10
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input matha10
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf matha10
! I can't find file `matha10'.
<*> ...=ljfour; mag:=1; nonstopmode; input matha10
                                                  
Please type another input file name
! Emergency stop.
<*> ...=ljfour; mag:=1; nonstopmode; input matha10
                                                  
Transcript written on mfput.log.
grep: matha10.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input matha10' failed to make matha10.tfm.
kpathsea: Appending font creation commands to missfont.log.

! Font U/matha/m/n/10.95=matha10 at 10.95pt not loadable: Metric (TFM) file not
 found.
<to be read again> 
                   relax 
l.31 $\boxplus
              $ something $\bigbox$ something $\bigboxplus$
? 


And it gets hung up on \boxplus, which has been working fine.

After removing \boxplus, it hangs on \bigboxplus (the one I want):

> zsharon@Weierstrass:~/UTSA/Algebra II/latex files$ latex sandbox2.tex ; dvipdf sandbox2.dvi ; evince sandbox2.pdf 
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./sandbox2.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, arabic, farsi, croatian, ukrainian, russian, bulgarian, czech, slov
ak, danish, dutch, finnish, basque, french, german, ngerman, ibycus, greek, mon
ogreek, ancientgreek, hungarian, italian, latin, mongolian, norsk, icelandic, i
nterlingua, turkish, coptic, romanian, welsh, serbian, slovenian, estonian, esp
eranto, uppersorbian, indonesian, polish, portuguese, spanish, catalan, galicia
n, swedish, ukenglish, pinyin, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size11.clo))
(/usr/share/texmf-texlive/tex/latex/amsfonts/amssymb.sty
(/usr/share/texmf-texlive/tex/latex/amsfonts/amsfonts.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty))
(/usr/share/texmf-texlive/tex/latex/amscls/amsthm.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/graphics/dvips.def)))
(/usr/share/texmf-texlive/tex/latex/geometry/geometry.sty
(/usr/share/texmf-texlive/tex/xelatex/xetexconfig/geometry.cfg))
(/usr/share/texmf-texlive/tex/latex/fancyhdr/fancyhdr.sty)
(/usr/share/texmf-texlive/tex/latex/lastpage/lastpage.sty)
(/usr/share/texmf-texlive/tex/latex/jknapltx/mathrsfs.sty)

! LaTeX Error: File `mathabx.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name: /usr/share/temf-texlive/tex/generic/misc/mathabx.sty

! LaTeX Error: File `/usr/share/temf-texlive/tex/generic/misc/mathabx.sty' not 
found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name: /usr/share/texmf-texlive/tex/generic/misc/mathabx.sty
(/usr/share/texmf-texlive/tex/generic/misc/mathabx.sty
! I can't find file `mathabx.dcl'.
l.74 \input mathabx.dcl
                       
Please type another input file name: /usr/share/texmf-texlive/tex/generic/misc/mathabx.dcl
(/usr/share/texmf-texlive/tex/generic/misc/mathabx.dcl)) (./sandbox2.aux)
(/usr/share/texmf-texlive/tex/latex/amsfonts/umsa.fd)
(/usr/share/texmf-texlive/tex/latex/amsfonts/umsb.fd)
(/usr/share/texmf-texlive/tex/latex/jknapltx/ursfs.fd)kpathsea: Running mktextfm matha10
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input matha10
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf matha10
! I can't find file `matha10'.
<*> ...=ljfour; mag:=1; nonstopmode; input matha10
                                                  
Please type another input file name
! Emergency stop.
<*> ...=ljfour; mag:=1; nonstopmode; input matha10
                                                  
Transcript written on mfput.log.
grep: matha10.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input matha10' failed to make matha10.tfm.
kpathsea: Appending font creation commands to missfont.log.

! Font U/matha/m/n/10.95=matha10 at 10.95pt not loadable: Metric (TFM) file not
 found.
<to be read again> 
                   relax 
l.31 $\bigboxplus
                 $
? 


I tell it to proceed (by pressing enter), and it tries again and hangs:

> kpathsea: Running mktextfm matha6
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input matha6
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf matha6
! I can't find file `matha6'.
<*> ...:=ljfour; mag:=1; nonstopmode; input matha6
                                                  
Please type another input file name
! Emergency stop.
<*> ...:=ljfour; mag:=1; nonstopmode; input matha6
                                                  
Transcript written on mfput.log.
grep: matha6.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input matha6' failed to make matha6.tfm.
! Font U/matha/m/n/6=matha6 at 6.0pt not loadable: Metric (TFM) file not found.
<to be read again> 
                   relax 
l.31 $\bigboxplus
                 $
? 


If I tell it to ignore the error (by entering "q"), then it spews some messages that I don't understand and renders the file incorrectly (no big box plus):

> l.31 $\bigboxplus
                 $
? q
OK, entering batchmodekpathsea: Running mktextfm mathb10
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathb10
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf mathb10
! I can't find file `mathb10'.
<*> ...=ljfour; mag:=1; nonstopmode; input mathb10
                                                  
Please type another input file name
! Emergency stop.
<*> ...=ljfour; mag:=1; nonstopmode; input mathb10
                                                  
Transcript written on mfput.log.
grep: mathb10.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathb10' failed to make mathb10.tfm.
kpathsea: Running mktextfm mathb8
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathb8
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf mathb8
! I can't find file `mathb8'.
<*> ...:=ljfour; mag:=1; nonstopmode; input mathb8
                                                  
Please type another input file name
! Emergency stop.
<*> ...:=ljfour; mag:=1; nonstopmode; input mathb8
                                                  
Transcript written on mfput.log.
grep: mathb8.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathb8' failed to make mathb8.tfm.
kpathsea: Running mktextfm mathb6
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathb6
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf mathb6
! I can't find file `mathb6'.
<*> ...:=ljfour; mag:=1; nonstopmode; input mathb6
                                                  
Please type another input file name
! Emergency stop.
<*> ...:=ljfour; mag:=1; nonstopmode; input mathb6
                                                  
Transcript written on mfput.log.
grep: mathb6.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathb6' failed to make mathb6.tfm.
kpathsea: Running mktextfm mathx10
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathx10
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf mathx10
! I can't find file `mathx10'.
<*> ...=ljfour; mag:=1; nonstopmode; input mathx10
                                                  
Please type another input file name
! Emergency stop.
<*> ...=ljfour; mag:=1; nonstopmode; input mathx10
                                                  
Transcript written on mfput.log.
grep: mathx10.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathx10' failed to make mathx10.tfm.
kpathsea: Running mktextfm mathx10
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathx10
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf mathx10
! I can't find file `mathx10'.
<*> ...=ljfour; mag:=1; nonstopmode; input mathx10
                                                  
Please type another input file name
! Emergency stop.
<*> ...=ljfour; mag:=1; nonstopmode; input mathx10
                                                  
Transcript written on mfput.log.
grep: mathx10.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathx10' failed to make mathx10.tfm.
kpathsea: Running mktextfm mathx10
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathx10
This is METAFONT, Version 2.71828 (Web2C 7.5.6)

kpathsea: Running mktexmf mathx10
! I can't find file `mathx10'.
<*> ...=ljfour; mag:=1; nonstopmode; input mathx10
                                                  
Please type another input file name
! Emergency stop.
<*> ...=ljfour; mag:=1; nonstopmode; input mathx10
                                                  
Transcript written on mfput.log.
grep: mathx10.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input mathx10' failed to make mathx10.tfm.
zsharon@Weierstrass:~/UTSA/Algebra II/latex files$ 


I have already tried googling and searching this forum for help.

Ideas?

Thanks,
Zach

---

### Post by SnickerSnack on 2010-03-26
Bump from page 4.





edit @ jpeddicord: Thanks.

---

### Post by jpeddicord on 2010-03-26
*Thread moved to **Education & Science**.*

---

### Post by PC_load_letter on 2010-03-28
go to the terminal and type:
```
sudo texhash
```
You'll be asked to type your password then the latex files will be updated. Now, try again and let's know.

---

### Post by SnickerSnack on 2010-03-29
> **PC_load_letter said:**
> go to the terminal and type:
```
sudo texhash
```
You'll be asked to type your password then the latex files will be updated. Now, try again and let's know.

Thanks, that's what I needed.

Edit: That works well, and it compiles correctly and shows the symbol.  But, then I get this:

dvips: Font mathx10 at 8760 not found; scaling 600 instead.
dvips: Such scaling will generate extremely poor output.
dvips: Font mathb10 at 8760 not found; scaling 600 instead.

So, some of the other symbols (which previously worked fine, and continue to if I comment out the usepackage{mathabx}) do not display correctly.

I think mathx10.mf is in the correct place:

/usr/share/texmf-texlive/fonts/source/public/mathabx/mathx10.mf

I tried running texhash again, but the problem persists.  I'll try copying it to other places to see if I can find the right one.

---

