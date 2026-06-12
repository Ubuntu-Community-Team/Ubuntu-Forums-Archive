---
title: "Latex Unicode : missing .def for arabic ?"
date: 2008-06-10
forum: Education &amp; Science
---

### Post by cudjoe on 2008-06-10
Hola !

I was wondering where I could get this missing uni-6.def file Latex complains about.

Here is my piece of Unicode Latex code (save in a UTF8 file) :

```

\documentclass{article}
\usepackage{ucs}
\usepackage[utf8x]{inputenc}
\title{éèê &#1607;&#1607;}
\begin{document}
\maketitle
\end{document}

```

The small piece of Arabic is missing its def file :

```

! Package ucs Error: Unknown Unicode character 1607 = U+0647,
(ucs)                possibly declared in uni-6.def.
(ucs)                Type H to see if it is available with options.

 ...                                              
                                                  
Unicode character 1607 = U+0647:
ARABIC LETTER HEH
ARABIC LETTER HA
Character is not defined in uni-*.def files.

```

I looked at /usr/share/texmf-texlive/tex/latex/ucs/data/ and it is not there.


Where can I get it ?

Should I fill a bug report on Launchpad ?

Thank you all for your patience.

---

### Post by hugmenot on 2008-06-10
That file seems to not exist.
But I think you want to use XeTeX, the sister compiler to PDFTeX. It is very well suited for unicode and scripts like arabic.
[www.tug.org/TUGboat/Articles/tb27-2/tb87kew.pdf](www.tug.org/TUGboat/Articles/tb27-2/tb87kew.pdf)

---

### Post by cudjoe on 2008-06-11
Thanks for your answer.

Your example looks very nice indeed.

However, I was investigating a way to get Arabic characters in Matplotlib. It looked like the only way was Latex.
No idea if I can use XeTeX in Matplotlib.

[http://www.mail-archive.com/matplotlib-users@lists.sourceforge.net/msg04645.html](http://www.mail-archive.com/matplotlib-users@lists.sourceforge.net/msg04645.html)

---

### Post by hugmenot on 2008-06-12
I don't know what they do to get the output into the plot.
This link is very confusing. Do they process the dvi, or the ps, or the pdf?.
[http://www.scipy.org/Cookbook/Matplotlib/UsingTex](http://www.scipy.org/Cookbook/Matplotlib/UsingTex)

You could set matplotlib to svg output and then edit the result in Inkscape to add r-t-l text there. Inkscape's text engine is Pango based, so I guess it is okay for this.

---

### Post by cudjoe on 2008-06-25
matplotlib text layout engine is pretty rough. The generated strings in the SVG are not text objects. They are split into letters.
This is too much SVG manipulation.

I'll get in touch with matplotlib guyz to see what they think about Xetex

---

### Post by mdboom on 2008-06-25
To answer your question about matplotlib's usetex functionality.  matplotlib includes text from LaTeX by using 'latex' to produce .dvi and then either:

  - if producing a bitmap, use "dvipng" to insert a bitmap into the plot

  - if producing a Ps or Pdf file, using "dvips" to get a vectorized version of the text and inserting that

As for matplotlib's SVG output, by default, it saves individual characters as paths so that the SVG is portable to other systems where the particular fonts may not be installed.  (SVG fonts would be better for this, but client support for them is patchy...)  This behavior can be turned off, however, by setting "svg.embed_char_paths" to "False".

---

### Post by cudjoe on 2008-06-25
Thank you so much mdboom !
Arabic layout in SVG works great ! Without adding **style="orientation:rtl"**. (at least with Inkscape)

 
I will check out with pycairo to export from SVG and let you know.

---

### Post by mnajem on 2009-10-05
Hello,

I used ArabTeX package for arabic character... I never use XeTeX, but it seems work for me


[IMG]http://kict.iiu.edu.my/~najmi/ucap-raya.PNG[/IMG]

---

### Post by rumpeltux on 2009-12-01
You can&#8217;t get it to work with ucs, but it&#8217;s right, that it works with ArabTex like that:

```
\documentclass{article}
\usepackage{arabtex}
\usepackage{utf8}

\begin{document}
\setcode{utf8}
\setarab
\RL{ &#1587;&#1604;&#1575;&#1605; }
\end{document}
```

And you&#8217;d need to install texlive-lang-arab to get the package.

See also: [http://itooktheredpill.dyndns.org/2009/arabic-script-in-latex/](http://itooktheredpill.dyndns.org/2009/arabic-script-in-latex/)

---

