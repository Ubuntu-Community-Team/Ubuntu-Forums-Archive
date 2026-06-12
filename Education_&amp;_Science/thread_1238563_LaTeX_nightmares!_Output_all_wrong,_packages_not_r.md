---
title: "LaTeX nightmares! Output all wrong, packages not recognized..."
date: 2009-08-12
forum: Education &amp; Science
---

### Post by Muiske on 2009-08-12
Hi there,


Being fed up with WYSIWYG type writers, I found the beauty and handiness of LaTeX. Now, having learned most of the document structures and commands that come with using LaTeX, I learned that installing the whole LaTeX system on Linux should be cake. That being said, I installed most of the texlive packages and started writing 'practice'-documents in Gedit (my text editor of choice). 

When I tried to create the dvi of this document (at the command-line with "tex filename.tex", I got several error messages starting with:

```
(./LaTeX_oefentekst.tex
! Undefined control sequence.
l.1 \documentclass
                  [a4paper, 12pt, notitlepage]{report}
? 
! Undefined control sequence.
l.2 \usepackage
               {amsmath}
? 
! Undefined control sequence.

```

What does this mean? Can anyone tell what I'm doing wrong?


Thanks,

Muiske.

---

### Post by unutbu on 2009-08-12
Try:
```
latex filename.tex
```

(tex is the lower-level command; latex is built on top of tex and provides some higher-level commands. Your manuscript appears to be using latex code.)

---

### Post by Chronon on 2009-08-12
Hi.

I actually have never used plain TeX.  One possibility is that \documentclass is a LaTeX macro and the tex compiler is complaining because it doesn't recognize it.

Try compiling with the latex compiler instead.

---

### Post by perroazul on 2009-08-12
could you post your file here (or at least the header and first paragraph of text)?

that way we could try compiling it and see what's going on. If it compiles correctly then it could be some problem with your installation.

---

### Post by Chronon on 2009-08-13
\usepackage is only allowed in plain TeX if you load Eplain macros first by doing \input eplain.  However, amsmath is not one of the packages you can load this way as far as I know.

I am 95% certain that your problems are due to trying to use the plain tex compiler on a latex document.

---

### Post by lethalfang on 2009-08-13
> **Muiske said:**
> Hi there,


Being fed up with WYSIWYG type writers, I found the beauty and handiness of LaTeX. Now, having learned most of the document structures and commands that come with using LaTeX, I learned that installing the whole LaTeX system on Linux should be cake. That being said, I installed most of the texlive packages and started writing 'practice'-documents in Gedit (my text editor of choice). 

When I tried to create the dvi of this document (at the command-line with "tex filename.tex", I got several error messages starting with:

```
(./LaTeX_oefentekst.tex
! Undefined control sequence.
l.1 \documentclass
                  [a4paper, 12pt, notitlepage]{report}
? 
! Undefined control sequence.
l.2 \usepackage
               {amsmath}
? 
! Undefined control sequence.

```

What does this mean? Can anyone tell what I'm doing wrong?


Thanks,

Muiske.


Are you trying LaTeX for the first time?
Maybe you should try an editor that's more geared toward latex, such as Kile, TeXMaker, etc, which you can compile in the text editor. 
... if you install Kile, you may install the version in Intrepid, as I've had crashing problems with the one shipped in Jaunty.

---

### Post by PC_load_letter on 2009-08-13
Welcome to the club, although if your documents have a lot of mathematical formulas, life can get a bit harder. 

First, regarding your error message, the control-sequence crap, I think it means that you're missing a ( or { somewhere to the point that Latex is confused. It's easier to spot the error by just knowing the line number, say if it is 20, then you look around that for typos.
IMHO, Latex has the worst syntax messages ever conceived. The other day I spent like 10 minutes staring at a very long formula to find the error, it was a missing or an extra }. The error message read something like "...line ended before \frac." :confused:

To me I resolve this by using editors with great autocomplete capabilities. I like Kile, Winefish, and Geany. In some of these editors (I think Geany), you can make it close the parentheses for you. 
make sure to check TexMaker, there is a new version that was released very recently, it's not in the repos but they have a deb package.

Best.

---

### Post by XCan on 2009-08-13
But the OP's issue is still probably because he runs tex instead of latex. Besides, math formulaes are a huge reason to use Latex. Sure matrices and arrays can be a pain to input, but clicking 1 million times in different boxes in WYSIWYG editors aren't fun either, and they typeset it like a three-year-old kid has written it.

---

### Post by PC_load_letter on 2009-08-13
XCAN: I wasn't really saying there are any better options than Latex, "WYSIWY don't usually G" option is much worse I agree, but come on, the error messages that Latex produces aren't really that clear most of the time, and if you are writing a thesis for a Mathematics graduate degree, as in my case, it gets a little unproductive & frustrating after a while. 

One way to go around this is IMO, as I mentioned, using Latex IDEs with good autocomplete features. The newest Kile version for Ubuntu 9.04 in the repos is really impressive. Lyx seems to be v. good as it now displays the equations inline, but I haven't really spent that much time with it.

---

### Post by XCan on 2009-08-13
Hehe yah, the error messages can be total nonsense sometimes. But still, you probably noticed that it gets better with time. I started off with Miktex and texmaker, by the time I made the switch to Ubuntu I started doing everything in gedit with the latex plugin. It's probably just me, but I really hate fluffy stuff when they are not needed. :)

---

### Post by samden on 2009-08-13
[B]Muiske:

Just type "latex filename.tex" instead of "tex filename.tex"

It really is that simple.[/B]

XCan: I'm similar, started in TeXShop on the Mac, moved to Ubuntu and tried Texmaker for a while before going to Gedit. The simpler the better!

---

### Post by Muiske on 2009-08-14
Thanks people for your suggestions.

@unutbu: this is what happens when I use latex:

```
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./LaTeX_oefentekst.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, arabic, farsi, croatian, ukrainian, russian, bulgarian, czech, slov
ak, danish, dutch, finnish, basque, french, german, ngerman, ibycus, greek, mon
ogreek, ancientgreek, hungarian, italian, latin, mongolian, norsk, icelandic, i
nterlingua, turkish, coptic, romanian, welsh, serbian, slovenian, estonian, esp
eranto, uppersorbian, indonesian, polish, portuguese, spanish, catalan, galicia
n, swedish, ukenglish, loaded.
(/usr/share/texmf-texlive/tex/latex/base/report.cls
Document Class: report 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty))
(./LaTeX_oefentekst.aux))
Runaway argument?
{De tweede paragraaf. We gaan gewoon door met lullen! Eens proberen o\ETC.
! File ended while scanning use of \@xdblarg.
<inserted text> 
                \par 
<*> LaTeX_oefentekst.tex
                        
? 

```

I don't know what this means. So... still a mess. :(


@perroazul: this is the beginning of the file:

```
\documentclass[a4paper, 12pt, notitlepage]{report}
\usepackage{amsmath}
\begin{document}
\begin{abstract}Dit is een oefenbestand voor \LaTeX{} om de basiscommando's te oefenen. Basiscommando's om een documentclass te kiezen en het begin en einde van een document te commanderen. Ja, en zo nog wat dingen, zoals een paragraaf indelen enzovoorts. Kortom, een beetje \`spielerei\', met -hoop ik-, het doel om langzaamaan een bekwame meester te worden in \LaTeX{}.\end{abstract}

\paragraph{De eerste paragraaf. Wat moeten we hier nu neerzetten?}

Dat was het!

\end{document}
```

Never mind the text, it's just some rubbish to practice around a bit. 

@Chronon: Ok, thanks. I think that's what the other posters tried to tell me. Do you know a solution for this? As you see, using the "latex" command doesn't really work either...

@lethalfang: I am currently using TexMaker. Still the same errors, though.

@PC_load_letter: Thanks for the suggestion! I'll make sure to look for missing brackets. And try using TexMaker (although I like the 'old school' method of using just a plain text editor).

---

### Post by XCan on 2009-08-14
I just tried your .tex file with both latex and pdflatex, both finished successfully, giving the following output

```
$ latex test.tex 
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./test.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/report.cls
Document Class: report 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty))
No file test.aux.
[1] (./test.aux) )
Output written on test.dvi (1 page, 1100 bytes).
Transcript written on test.log.

```

```
$ pdflatex test.tex
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./test.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/report.cls
Document Class: report 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty)) (./test.aux) [1{/var/l
ib/texmf/fonts/map/pdftex/updmap/pdftex.map}] (./test.aux) )</usr/share/texmf-t
exlive/fonts/type1/bluesky/cm/cmbx10.pfb></usr/share/texmf-texlive/fonts/type1/
bluesky/cm/cmbx12.pfb></usr/share/texmf-texlive/fonts/type1/bluesky/cm/cmr10.pf
b></usr/share/texmf-texlive/fonts/type1/bluesky/cm/cmr12.pfb></usr/share/texmf-
texlive/fonts/type1/bluesky/cm/cmr8.pfb>
Output written on test.pdf (1 page, 27115 bytes).
Transcript written on test.log.
```

Did you write that text in gedit or did you use some other text editor? Perhaps you're getting some invisible chars if you use some strange editor.

---

### Post by Chronon on 2009-08-15
> **Muiske said:**
> 

```

(./LaTeX_oefentekst.aux))
Runaway argument?
{De tweede paragraaf. We gaan gewoon door met lullen! Eens proberen o\ETC.
! File ended while scanning use of \@xdblarg.
<inserted text> 
                \par 
<*> LaTeX_oefentekst.tex
                        
? 

```



@Chronon: Ok, thanks. I think that's what the other posters tried to tell me. Do you know a solution for this? As you see, using the "latex" command doesn't really work either...


Yes, but it fixed all of the previous problems.  You're seeing something entirely different now.  It mentions a .aux file.  You might try removing all of the .aux files and rebuild.  (Sort of like doing "make clean".)  I suspect it's left over from the failed previous attempt.

---

### Post by Muiske on 2009-08-15
@Xcan: Ok well, it seems to work now. As soon as I try to insert a tabular environment in TexMaker (according to "The Not So Short Introduction To LaTeX") the program hangs as soon as I press the 'latex' button... Do you have any tips on this? How should one insert tables in the document?

@Chronon: That's true. It seems to 'kind of' work now...

---

### Post by XCan on 2009-08-15
As I mentioned earlier, I don't use any fancy editor, I just check out the wikibook if I forget how to do something [http://en.wikibooks.org/wiki/LaTeX](http://en.wikibooks.org/wiki/LaTeX) . If I would do a table I would simply write the following by hand (or copy paste of course ;) )

```

\begin{table}
\centering
\caption{This is an ultra-cool table and it complies with all typographical norms.}
\label{tab:cool}

\begin{tabular}{lll}
\toprule
Time (s) & Velocity (m/s) & Pulse Energy (J) \\
\midrule
1 & 10 & 0.03 \\
2 & 10 & 0.03 \\
3 & 10 & 0.03 \\
4 & 10 & 0.03 \\
5 & 10 & 0.03 \\
\bottomrule
\end{tabular}

\end{table}

```

---

### Post by Chronon on 2009-08-17
Yes, I write using gedit and build with rubber.

---

### Post by samden on 2009-08-17
Muiske: You probably ended up with odd .aux files after trying to use tex instead of latex earlier. I'd say that was the whole problem all along. This meant that not only did you have to start using the latex command, you also had to remove all traces of your previous use of the tex command (the .aux files).

I'd recommend you download ["The not-so-short introduction to LaTeX"]("http://tobi.oetiker.ch/lshort/lshort.pdf"), which will tell you everything you need to get started and produce most documents. As you get more advanced, you may also find the ["LaTeX guide for authors"]("http://www.latex-project.org/guides/usrguide.pdf") useful - it has a full list of all LaTeX commands and what they do.

Don't give up on it just because you made a little mistake at the beginning, it's a steep learning curve for the first few days but well worth it! :)

---

### Post by Muiske on 2009-08-19
Thanks everyone for your help! :)

@samden: I'm not giving up, on the contrary! :)

---

