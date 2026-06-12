---
title: "LaTeX: one figure per page at the end of a paper"
date: 2009-09-21
forum: Education &amp; Science
---

### Post by lethalfang on 2009-09-21
How do I force LaTeX to put exactly one figure per page after the main article?
I've tried \newpage, \pagebreak, and \vfill\eject after each figure, as well as \begin{figure}[p], and many combinations of the above, but none of them worked. LaTeX still put more than one figure on one page if the figures fit. 

Thanks

---

### Post by XCan on 2009-09-21
\newpage is a bit dodgy. I've had luck using
```

\newpage
~
\newpage

```

Oh, there's probably a very reasonable explanation for this, but I never cared to look it up. :p

---

### Post by ahmatti on 2009-09-22
Use endfloat: [http://www.ctan.org/tex-archive/help/Catalogue/entries/endfloat.html](http://www.ctan.org/tex-archive/help/Catalogue/entries/endfloat.html), it will do exactly what you want and optionally leave markers in text as a placeholder. You can also (optionally) place tables in the end of the document and create list of figures and tables in correct location.

---

### Post by quantasham on 2011-02-12
That is of great help, ahmatti. Yet I am facing another problem - the figure number goes like: 

Figure 3.1, Figure 3.2,... 

because my document is divided into chapters. Instead, I want it to be

Figure 1, Figure 2,...

what modification I should make?

Here is the minimal .tex that illustrates my difficulty:

\documentclass[pdftex,letterpaper]{report}
\usepackage[dvips]{graphicx}
\usepackage[nofiglist]{endfloat}
\begin{document}
\newpage
\chapter{Review}
this is chapter 1
\newpage
\chapter{Theory}
this is chapter 2. See Fig.~\ref{CVDSC}.
\begin{figure}
\centering
\includegraphics[width=0.8\textwidth]{CVDSC.png}
\caption{\label{CVDSC}funny weird caption.}
\end{figure}
\newpage
\chapter{Conclusion}
Last chapter
\end{document}

---

### Post by agm. on 2011-02-13
Two points:

To the original problem, I've used the command \clearpage quite well.  After each figure, just use \clearpage and it puts one figure per page.

To the other problem regarding figure numbers.  Here's the command that someone taught me, which I use when having to do things like Appendices and such.

\renewcommand{\thetable}{A-\arabic{table}}
\setcounter{table}{0}

So you should be able to use the exact command to label your tables as:

\renewcommand{\thetable}{\arabic{table}}
\setcounter{table}{0}

Right before your figure... I haven't tried it in the chapter format, but the using the renewcommand should work.  

Hope that helps!

---

### Post by quantasham on 2011-02-13
It works. Thanks, agm. All I did was replacing all "table" in your code with "figure".

---

### Post by frisket on 2011-02-19
> **lethalfang said:**
> How do I force LaTeX to put exactly one figure per page after the main article?
I've tried \newpage, \pagebreak, and \vfill\eject after each figure, as well as \begin{figure}[p], and many combinations of the above, but none of them worked. LaTeX still put more than one figure on one page if the figures fit.

That's because the default document classes say so. For example, article.cls says:

```

\setcounter{topnumber}{2}
\renewcommand\topfraction{.7}
\setcounter{bottomnumber}{1}
\renewcommand\bottomfraction{.3}
\setcounter{totalnumber}{3}
\renewcommand\textfraction{.2}
\renewcommand\floatpagefraction{.5}

```

Just copy the relevant lines into your Preamble and change the values to suit.

---

### Post by nan-tze on 2011-09-09
Hi, 

I'm also trying to put one figure to a page, but I want the figures to go in the text, not all at the end of the chapter (it's a long chapter.) 

-This means endfloat won't help

-Using \newpage or \clearpage after a figure also puts a pagebreak in the text, leaving a half-empty page, which looks bad.

- \begin{figure}[p] and [!p] don't seem to have any effect

- \setcounter{totalnumber}{1} also seems to have no effect, whether in the preamble or in the text. 

Can anyone help?? 

Thanks for all the other suggestions so far!

---

### Post by FreeTheBee on 2011-09-11
I think this should give the right result,

```

\begin{figure}
\begin{minipage}[c][\textheight]{\textwidth}
\includegraphics[width=\figwidth]{figname}
  \caption{this is a figure}
  \label{fig:afigure}
\end{minipage}
\end{figure}

```

---

### Post by nan-tze on 2011-09-11
Thanks freethebee, that does exactly what I want it too! 

N

---

### Post by wera on 2012-06-14
```
\begin{figure}[h]
```

Figures
To create a figure, you must use the figure environment (tricky, eh?!).

\begin{figure}[placement specifier]
... figure contents ... 
\end{figure}

Specifier	Permission
h	Place the float here, i.e., at the same point it occurs in the source text.
t	Position at the top of the page.
b	Position at the bottom of the page.
p	Put on a special page for floats only.
!	Override internal parameters LaTeX uses for determining `good' float positions.

---

