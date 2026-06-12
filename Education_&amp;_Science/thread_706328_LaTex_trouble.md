---
title: "LaTex trouble"
date: 2008-02-24
forum: Education &amp; Science
---

### Post by Chepe on 2008-02-24
I've been using LaTex a lot lately on school, but now I would like to get it going on my own computer as well. 
I have two main problems:

1. I use the package listings to include graphics, however when I try to include an .eps picture I get an error message saying : "Unknown graphics extension: .eps". 
(I use pdflatex to compile.) What can I do to get this to work?

2. I want to make my CV in latex, and I've found some good templates. However, when I try to compile I get the error message: "XeTex is required to compile this document." However I have downloaded texlive (sudo apt-get install texlive -full) which is a 700mb package, and I've read that this package is supposed to include XeTex. Does anyone know what I can do to fix this? Do I need to configure something?

I appreciate all help!

---

### Post by GreaterCore on 2008-02-24
I've been using LaTex a lot lately on school, but now I would like to get it going on my own computer as well. 
I have two main problems:

> **Chepe said:**
> 1. I use the package listings to include graphics, however when I try to include an .eps picture I get an error message saying : "Unknown graphics extension: .eps". 
(I use pdflatex to compile.) What can I do to get this to work?
This sounds familiar, I had the same problem on a Windows machine once. Turns out pdflatex takes in PDF extensions but not EPS, while latex takes in EPS but not PDF. Quick way is to convert using ''epstopdf'', you can ''apt-get'' that package. Best is not to put an extension. Depending on your compiler, it will automatically look for usable file type. Another method is to compile it to PS and then use something like ''ps2pdf''. However, this may rasterize some of your pretty graphs (as I have encountered it myself) and may look horrible when zoomed in close enough.

> **Chepe said:**
> 2. I want to make my CV in latex, and I've found some good templates. However, when I try to compile I get the error message: "XeTex is required to compile this document." However I have downloaded texlive (sudo apt-get install texlive -full) which is a 700mb package, and I've read that this package is supposed to include XeTex. Does anyone know what I can do to fix this? Do I need to configure something?
I have not encountered this, perhaps you may want to post the URL where you have gotten this from. I could download and try it out when I'm free. Sorry.

---

### Post by Chepe on 2008-02-24
Perfect! I tried now to use "epstopdf" and then compile and it works great! 
I've been trying to find a solution for a while, so thanks a lot!

Would be great if you could try to compile, the link is: 
[http://nitens.org/taraborelli/cvtex](http://nitens.org/taraborelli/cvtex)

I'm trying to compile number 2. Gentium Basic.

---

### Post by LaserJock on 2008-02-24
> **GreaterCore said:**
> I've been using LaTex a lot lately on school, but now I would like to get it going on my own computer as well. 
I have two main problems:


This sounds familiar, I had the same problem on a Windows machine once. Turns out pdflatex takes in PDF extensions but not EPS, while latex takes in EPS but not PDF. Quick way is to convert using ''epstopdf'', you can ''apt-get'' that package. Best is not to put an extension. Depending on your compiler, it will automatically look for usable file type. Another method is to compile it to PS and then use something like ''ps2pdf''. However, this may rasterize some of your pretty graphs (as I have encountered it myself) and may look horrible when zoomed in close enough.

pdflatex also takes .pngs . I ran into this same problem when I started my dissertation and decided to go with pdflatex over latex.

-LaserJock

---

### Post by northern lights on 2008-02-24
As far as the .eps files are concerned, [this]("http://www.utexas.edu/ogs/etd/LaTeX/Figures+Graphics+PS/include.ps.in.latex.ps") should solve your problem.

---

### Post by xadder on 2008-02-25
I am not sure why this works, but I still use latex with .ps and .eps files. I don't convert to pdf or png.

I'm using tex-live, with everything installed by synaptic on a gutsy system.

---

### Post by Chepe on 2008-02-25
That's strange, that's the same as I have done... 
But It works for me now if I first convert .eps to .pdf.

If you download one of the cv templates from this page (for example number 2.) are you able to compile it?

---

### Post by xadder on 2008-02-25
Ah, those templates need new packages (xetex, which I had never hward of). I had a quick try (installed xetex through synaptic), but something doesn't work. To me it looks as though xetex is the problemn, not latex!

I note that though that the cv example file uses dvipdfm and other pdf features, but isn't using the graphicx package I would normally use, e.g.

\documentclass[]{article}
\usepackage{graphicx}

\begin{document}
   \includegraphics[width=4cm]{TEST.eps}
\end{document}

Sometimes I have dvips as an argument to graphicx, but I can't remember when and why just now.

---

### Post by Chepe on 2008-02-25
I think you're right, xetex seems to be the problem. I think I'll just search around a bit for another template :)

Thanks for the help!

---

### Post by NikoC on 2008-02-28
And what if you first latex your complete document including the eps images to dvi and than from dvi to latex?

---

### Post by Typhoon on 2008-02-28
XeTeX was originally a Mac OS X only version of TeX using special fonts. I understand that it is now available for Linux, but you would probably find it easier to find a new template.

Typhoon

---

### Post by Chepe on 2008-02-29
Yeah, that seems like a good plan, I'll probably just search around a bit for a new template.

---

### Post by wnwek on 2008-02-29
pdflatex also takes jpgs, pngs, etc. but doesn't take eps format images. That's all you need to remember.

---

### Post by hugmenot on 2008-03-02
Hi, some clues:

[LIST]
[*]latex: the old processor. Outputs .dvi. DVI has to be converted two more times to get a PDF file (dvi&#8594;ps&#8594;pdf). Allows EPS graphics as input. No fancy features besides direct support of PostScript.
[*]pdflatex: the PDFTeX based processor. Outputs .pdf directly. Has some nice typographical features like margin kerning and a [hz-like algorithm]("http://en.wikipedia.org/wiki/Hz-program"). Accepts, PNG, JPG, and PDF as graphic formats directly. 
[*]xelatex: the alternative to pdflatex. It is based on XeTeX, which proposes an alternate route to font handling, typography, an internationalization, Unicodee, etc. Accepts the same graphics as PDFTeX, but can use own graphics code.
[/LIST]

This means that for your CV template you would process it with
```
xelatex cv.tex
```
and not pdflatex. It's a different system. It's cool, really.

---

