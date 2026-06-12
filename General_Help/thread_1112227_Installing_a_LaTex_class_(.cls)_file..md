---
title: "Installing a LaTex class (.cls) file."
date: 2009-03-31
forum: General Help
---

### Post by redders on 2009-03-31
Hi everyone,

I'm trying to install the 'exam' class for latex ([downloaded here](http://www.ctan.org/tex-archive/help/Catalogue/entries/exam.html)).

All of the instructions I have found apply either to .ins or .sty files.

I was wondering if someone would be able to give me a quick run through of what I have to do to get a .cls file working in LaTeX, or at least point me in the direction of somewhere I might find out about this?

Thanks very much!

---

### Post by mister_pink on 2009-03-31
I've never installed a .cls file but I suspect its similar.

Open a terminal and do 
```
locate article.cls
```
to find out where it belongs. Then copy your cls file to there
```

sudo cp yourclsfile.cls /usr/share/rest/of/the/path/from/above

```
Then you might need to update the tex database with "texhash"

Alternatively you can probably just put it in the same folder as your latex document!

---

### Post by redders on 2009-03-31
I feel out of my depth here!

When I ran pdflatex on my test document using the exam package, I get this:
```

! LaTeX Error: File `exam.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name: exam.cls
(/home/redders/texmf/tex/latex/exam/exam.cls

! LaTeX Error: Two \LoadClass commands.

```

---

### Post by redders on 2009-03-31
Answered my own question. I am a fool.

I have some documentation from a lecture saying I need to use the commannd:
```

\usepackage {packagename}

```

I assume this applies to packages, which are something different to classes. That was basically causing the class file to be used twice, hence the two \loadclass error. 

I removed that line, and instead used:

\documentclass {classname}

Thanks for the help and sorry for being a noob!

---

### Post by matyasfalvi on 2010-02-15
Hi All!

I have an issue with latex and I suspect it has something to do with my **.cls** file. 
I am trying to use the **puthesis.cls** and **thesis.tex** files (available [**_here_**]("http://www.math.princeton.edu/graduate/tex/puthesis.html")) in a latex project. (Trying to write my thesis in :D). 
I have all the files in the project in one folder including the **puthesis.cls** file, I also have copied the **puthesis.cls** file into the following folders: ```
/usr/share/texmf-texlive/tex/latex/base
```
and ```
/usr/share/texmf/tex/latex
```. I am using **thesis.tex** as the **master document**. 
When I try to Quickbuild the document I get this really strange one:
```
./thesis.tex:35:Undefined control sequence \begin{document}
```
```
./thesis.tex:35:File '.tex' not found. \begin{document}
```

Here is the complete output:

```

*****
*****     PDFLaTeX output: 
*****     cd "/home/george/Thesis"
*****     pdflatex -interaction=nonstopmode 'thesis.tex'
*****
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./thesis.tex
LaTeX2e &lt;2005/12/01&gt;
Babel &lt;v3.8h&gt; and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(./puthesis.cls
Document Class: puthesis 2008/05/02 v1.4.1 Princeton University Thesis class
(/usr/share/texmf-texlive/tex/latex/setspace/setspace.sty
Package: `setspace' 6.7 &lt;2000/12/01&gt;
) (/usr/share/texmf-texlive/tex/latex/base/report.cls
Document Class: report 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo)))
(/usr/share/texmf-texlive/tex/latex/graphics/epsfig.sty
(/usr/share/texmf-texlive/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-texlive/tex/latex/graphics/graphics.sty
(/usr/share/texmf-texlive/tex/latex/graphics/trig.sty)
(/etc/texmf/tex/latex/config/graphics.cfg)
(/usr/share/texmf-texlive/tex/latex/pdftex-def/pdftex.def))))
(/usr/share/texmf-texlive/tex/latex/amsfonts/amsfonts.sty)
(/usr/share/texmf-texlive/tex/latex/amsfonts/amssymb.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/share/texmf-texlive/tex/latex/amsmath/amstext.sty
(/usr/share/texmf-texlive/tex/latex/amsmath/amsgen.sty))
(/usr/share/texmf-texlive/tex/latex/amsmath/amsbsy.sty)
(/usr/share/texmf-texlive/tex/latex/amsmath/amsopn.sty))
(/usr/share/texmf-texlive/tex/latex/amscls/amsthm.sty)
(/usr/share/texmf-texlive/tex/latex/base/latexsym.sty)
(/usr/share/texmf-texlive/tex/latex/ucs/ucs.sty
(/usr/share/texmf-texlive/tex/latex/ucs/data/uni-global.def))
(/usr/share/texmf-texlive/tex/latex/ltxmisc/url.sty) (./thesis.aux)
! Undefined control sequence.
\maketitlepage ...\\ \@dept \\ Adviser: \@adviser 
                                                  \end {center} \vspace {.3i...
l.35 \begin{document}
                     
[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}]
(/usr/share/texmf-texlive/tex/latex/base/omscmr.fd) [2]

! LaTeX Error: File `.tex' not found.

Type X to quit or &lt;RETURN&gt; to proceed,
or enter new name. (Default extension: tex)

Enter file name: 
! Emergency stop.
&lt;read *&gt; 
         
l.35 \begin{document}
                     ^^M
!  ==&gt; Fatal error occurred, no output PDF file produced!
Transcript written on thesis.log.

```

My kile and karmic koala have just been installed 3 days ago so I also might be missing some additional packages that I don't know about. However simple documents with **class article** (**article.cls**) are compiled without errors. 

Any help is much appreciated!
Thanx a lot!

---

### Post by Abdus on 2010-02-15
Really hard to help without the source file, i.e. the master document (without your thesis content).

On the first glance it seems to me you have "begin{document}" included twice or that you put some text before the "begin{document}" - for example the "\maketitlepage" macro.

---

### Post by matyasfalvi on 2010-02-16
Hi Abdus!

Thank you for your answer! 

I want to use the thesis.tex file as the master document available from here: [http://www.math.princeton.edu/graduate/tex/puthesis.html]("http://www.math.princeton.edu/graduate/tex/puthesis.html"). But I have uploaded it as well. You can find the puthesis.cls file and a sample file on the website. I'm just about to start my thesis so I didn't alter the file that is provided on the website still it doesn't work so this is the reason why this is really strange to me. 

Thank you for your help!

---

### Post by matyasfalvi on 2010-02-16
I'm sorry some how it didn't go through. So here is the file.

---

### Post by Abdus on 2010-02-16
Well... The class you're trying to use, suggested by your school, is just wrong - it's awfully written, full of traps and is very badly documented. The sample file they provide does not even work with the class... Long time since I saw such a wrong implementation of LaTeX class. :)

The cause of your problem is lack of the above lines in your document:
```
\adviser{My Adviser}
\abstract{The abstract goes here.}
\acknowledgements{Thank you very much.}
\dedication{To myself.}
```
As soon as you add them, it will work.

This is because the \maketitlepage macro defined in the class file demands the values for "\adviser" and so on to be defined. If they are not defined, the macro breaks and produces an error message.

PS. And they even say "%% You are *not* allowed to modify this file." in the .cls file. Truly ridiculous. You don't have right to modify it... yet it consists of only 140 lines of very simple code... Very strange thing as for a university, indeed.

---

### Post by matyasfalvi on 2010-02-17
Hi Abdus!

Thank you for your answer! I am really grateful for your help. It does work now with the lines added this is really great. 

Well the thing is that we don't actually have to use this class, we can use any class we wish. So in case you have any ideas where I could find something more usable I would love to hear them. (Is there may be a sort of GNU database?)

I myself looked up two more:
[http://www.math.dartmouth.edu/~ahb/thesis/format.html](http://www.math.dartmouth.edu/~ahb/thesis/format.html)
[http://amath.colorado.edu/documentation/LaTeX/thesis/source/thesis.cls](http://amath.colorado.edu/documentation/LaTeX/thesis/source/thesis.cls)

I'll see how they work.

Thank you very much for your help. I really appreciate it!

Take care!

---

