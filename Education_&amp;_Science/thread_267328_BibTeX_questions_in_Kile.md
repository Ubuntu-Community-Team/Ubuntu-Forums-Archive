---
title: "BibTeX questions in Kile"
date: 2006-09-28
forum: Education &amp; Science
---

### Post by madcow72 on 2006-09-28
Hello!  I'm a noobie to Linux and am still crossing over from Windows to Linux programs.  I used to use WinEdt - MikTeX for all my LaTeX editing in Windows, and am learning to use Kile under Kubuntu.  So far I really like the program, but need to resolve 2 problems in regard to BibTeX:

1)  Is there any way to coerce Kile to bring up the popup menu of authors from my bibliography when I type: \cite{}?  

(This is not so essential, but would be very nice)

2)  When I compile a sample document with a citation, I get the following errors in Output:
```
Package natbib Warning: Citation `Biancaniello_2005' on page 1 undefined on input line 41.
Package natbib Warning: There were undefined citations.
```

I feel like the error must be somewhere in my Kile configuration, but just in case it's within my document, a minimal example looks like:
```
\documentclass[twocolumn,preprintnumbers,amsmath,amssymb,prb]{revtex4}
\usepackage{dcolumn}
\usepackage{bm}
\usepackage{natbib}
\usepackage[dvips]{graphicx}
\usepackage{floatflt}
\bibliographystyle{achemso} 
\begin{document}
\title{A Wonderful Article}
\author{T.L. Jennings}
\maketitle
The use of microbead carriers for genomic detection is really cool.\cite{Biancaniello_2005}
\bibliography{ubead}
\end{document}

```

I'm positive that the label is correct in both the document and the ubead bibliography.  The pdf output shows the correct citation at the bottom of the page, but gives only a superscripted question mark within the document as a reference to this citation.

Any help or suggestions would be great!

---

### Post by dwight on 2006-09-28
Haven't used bibtex with Kile, but usually with this 'undefined citations' error it helps to run bibtex a couple of times. There's probably a menu item or a button for that in Kile.

---

### Post by madcow72 on 2006-09-28
Thanks for the suggestion Dwight!  It's actually habit for me to Latex-Bibtex-Latex-Latex coming from WinEDT, (I don't know if that's necessary the way Kile compiles or not, but I know it doesn't hurt.)  Unfortunately, that doesn't solve the problem.  

I'm sure the answer to this problem is something simple like that, but I haven't found it yet.

---

### Post by NoNo_231 on 2006-09-28
Miktex is a little bit different. I believe that you have installed, if not all, many packages, but under ubuntu, there are only few common packages installed in tex. That means that you have to install the ones you want by yourself, if they are not installed. If you already done that then 

Try first running latex twice, if you haven't done so, then bibtex twice and again latex twice. then pdflatex.

Also you could try texmaker for editing latex, or emacs.

there also programs for bibtex as pybliographic bibliography manager (in synaptic), or jabRef, which it says that it can import bibliography to kile or lyx, and to the WinEdt which you used. Hever tried. There is a deb package or download the jar package if you have java installed.

---

### Post by dwight on 2006-09-28
Recently I had a very similar problem with latex/bibtex. I'm not using any IDE for that though (of course some might call gvim+latex-suite and IDE :)). The thing was that regardless of the number of times I ran latex and bibtex on a file I still had questionmarks in text and 'undefined citation' errors. What helped was deleting all the temporary files latex and bibtex create (aux,bbl,blg,...). But, I think that Kile should be able to handle that on its own. Still, you might want to give NoNo's suggestion a try in the terminal (after removing the temp files) - 2x latex, 2x bibtex, latex ,...

---

### Post by madcow72 on 2006-09-28
Thank you both for your suggestions!  

Because WinEDT could also be problematic regarding the number of times one compiles, I've actually tried numerous combinations of Latex-Bibtex commands - but alas.

Also, your suggestion about deleting the .bbl and .aux files is definitely a good one.  However, already gave this a try and no change.  Since this is my first time using Kile, I'm curious: does BibTeX work right "out-of-the-box" for most Kile users?  (Anyone out there using Kile? Please let me know!)  I suppose in the end, I could write the entire document and manually replace all the question marks with numbers for the end pdf...but I'd really rather not.

I'm going to try installing some of the bibliography packages NoNo mentioned tomorrow when I get back to my work computer.

---

### Post by NoNo_231 on 2006-09-29
kile and texmaker, which I worked with are only some editors with good highlighting button-macros for the tex commands. when latex from kile is called if it has secondary errors goes on, if it has a primary eror stops.

you could try using the latex, pdflatex, bibtex commands from a terminal and  probably you could see more on your problem.

There are some packages in synaptic, try out, if there is one of the packages you need. Otherwise you have to download and install what you want manually.

You could also try - experimentally for start - another bibliography style to see if it works.

---

### Post by julian_tejada on 2008-04-05
Hi, Kile din't take the command to create the bbl file from bib file, but it is simple, in the console digit the command:

bibtex "name of the file .tex"

after that return to the kile and use it in the normal way.

---

### Post by rosencrantz on 2008-10-14
Kind of a late reply - but did you check out the QuickBuild options in Kile->Settings?
PDFLaTeX+BibTeX isn't preconfigured (at least with my Kile version) and has to be added by hand (pdflatex, bibtex, pdflatex, pdflatex). After that, you can run everything from inside Kile with the QuickBuild button.
If you are using a Kile project with a master document, you have to specify the appropriate QuickBuild type in the Project Options dialog.

Cheers, rosencrantz

---

