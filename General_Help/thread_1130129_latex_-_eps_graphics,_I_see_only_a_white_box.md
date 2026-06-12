---
title: "latex - eps graphics, I see only a white box"
date: 2009-04-19
forum: General Help
---

### Post by finalsayan on 2009-04-19
I everybody,
I started using latex today
I have installed texlive and kile for editing

I have tried to make my first latex document just including a graphic, but everything that I see is a white box
you have suggestion? :( :(

this is my simple latex file and then what I see

```

\documentclass[12pt,a4paper]{report}

\usepackage{graphics,graphicx,epsfig}
\usepackage[italian]{babel}
\usepackage{latexsym}

\pagestyle{headings}

\begin{document}

\begin{figure}
\psfig{figure=density.eps}
\caption{Vertici-Densit\`a-Cutset  sulla nostra test suite} 
\label{densityfig}
\end{figure}

\end{document}

```

kile output

```

[LaTeX] relazionelatex.tex => relazionelatex.dvi (latex)
/usr/share/texmf-texlive/tex/generic/babel/italian.ldf:0: No hyphenation patterns were loaded for(babel) the language `Italian'(babel) I will use the patterns loaded for \language=0 instead.
./relazionelatex.tex:0:No file relazionelatex.aux.
./relazionelatex.tex:0: Label(s) may have changed. Rerun to get cross-references right.
[LaTeX] 0 errors, 3 warnings, 0 badboxes
[LaTeX] Done!

[LaTeX] relazionelatex.tex => relazionelatex.dvi (latex)
/usr/share/texmf-texlive/tex/generic/babel/italian.ldf:0: No hyphenation patterns were loaded for(babel) the language `Italian'(babel) I will use the patterns loaded for \language=0 instead.
[LaTeX] 0 errors, 1 warning, 0 badboxes
[LaTeX] Done!

[ViewDVI] relazionelatex.dvi (kdvi)
[ViewDVI] finished with exit status 127

```

and what I see

---

### Post by mali2297 on 2009-04-19
First, rerun latex as suggested. Then try producing a PDF or PS file from the DVI, either through some menu in Kile or from the command line:
```

dvipdf relazionelatex.dvi

```

---

### Post by finalsayan on 2009-04-19
> **mali2297 said:**
> First, rerun latex as suggested. Then try producing a PDF or PS file from the DVI, either through some menu in Kile or from the command line:
```

dvipdf relazionelatex.dvi

```
you are right! in pdf I can see the graphics

in your opinion why I can't see the graphics in .dvi format? It is a problem of my latex compiler?

---

### Post by mali2297 on 2009-04-19
> **finalsayan said:**
> you are right! in pdf I can see the graphics

in your opinion why I can't see the graphics in .dvi format? It is a problem of my latex compiler?

I would rather think that it is a limitation of the DVI format. One seldom use DVI other than as an intermediate product during the creation of a PDF. As an alternative, you can create a PDF directly with pdflatex.

---

### Post by Stefan_K on 2009-04-30
Hi,

it's just a problem of the dvi viewer.
Btw. you don't need to load graphics, that will be done by graphicx already.

Instead of dvipdf you could use dvips and ps2pdf or the buttons of Kile labeled with DVItoPS and PStoPDF.

Stefan

--
[TeXblog.net]("http://texblog.net")

---

