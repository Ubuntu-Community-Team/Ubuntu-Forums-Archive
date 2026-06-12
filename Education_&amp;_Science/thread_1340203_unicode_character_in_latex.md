---
title: "unicode character in latex"
date: 2009-11-28
forum: Education &amp; Science
---

### Post by VCoolio on 2009-11-28
I'm just starting with latex, which means I can google for it all afternoon without getting it solved. So, how do I get, for example, unicode character 1d513 (that's a papyrus sign) in latex? Please provide me with everything, also the \usepackage part, I just don't get it.

---

### Post by Chronon on 2009-11-28
Maybe XeTeX is the ticket: [http://en.wikipedia.org/wiki/XeTeX](http://en.wikipedia.org/wiki/XeTeX)

It's part of TexLive distribution, so shouldn't be too much trouble to get going.  I believe the compiler is called "xelatex"

---

### Post by Alexandre Putt on 2009-11-29
::deleted::

---

### Post by VCoolio on 2009-11-29
Thanks for trying to help, I really appreciate it, but since I am a latex beginner I really can't do much with 'try xetex' or 'use that', because I don't know how and all the internet didn't provide me with a comprehensible answer, rant rant rant. 

But it is possible. A friend of mine accomplished the almost impossible task of putting one special unicode character in latex ( << sarcasm ) by using lyx and then checking the .tex file. Seems like \usepackage{amssymb} is the solution in this particular case, although I can't understand why I didn't read about this in a day long googling around.

```
\documentclass[english]{article}
%\usepackage[T1]{fontenc}
\usepackage[utf8x]{inputenc}
\usepackage{amssymb}
\usepackage{babel}

\begin{document}
\title{Unicode test}
\author{VCoolio}
\maketitle
\part{The big test}
\section{bla bla}
this is what it was all about: &#120083;
\end{document}
```

Anyway, biggest lesson is to take a break if something doesn't work and try again next day. Also latex really seems like an opportunity: gedit now has more features for me than any office suite.

---

### Post by zika on 2009-11-29
> **VCoolio said:**
> Thanks for trying to help, I really appreciate it, but since I am a latex beginner I really can't do much with 'try xetex' or 'use that', because I don't know how and all the internet didn't provide me with a comprehensible answer, rant rant rant. 

But it is possible. A friend of mine accomplished the almost impossible task of putting one special unicode character in latex ( << sarcasm ) by using lyx and then checking the .tex file. Seems like \usepackage{amssymb} is the solution in this particular case, although I can't understand why I didn't read about this in a day long googling around.

```
\documentclass[english]{article}
%\usepackage[T1]{fontenc}
\usepackage[utf8x]{inputenc}
\usepackage{amssymb}
\usepackage{babel}

\begin{document}
\title{Unicode test}
\author{VCoolio}
\maketitle
\part{The big test}
\section{bla bla}
this is what it was all about: &#65533;&#65533;
\end{document}
```Anyway, biggest lesson is to take a break if something doesn't work and try again next day. Also latex really seems like an opportunity: gedit now has more features for me than any office suite.{\goth B}
TeX should be (and is) as much machine dependent as possible ... Thank You Donald!
I did not mess with Your words in quoted text, You can see how it is problematic to use machine dependent symbols ...

---

### Post by frisket on 2009-11-29
> **VCoolio said:**
> Thanks for trying to help, I really appreciate it, but since I am a latex beginner I really can't do much with 'try xetex' or 'use that', because I don't know how and all the internet didn't provide me with a comprehensible answer, rant rant rant.

[LIST=1]
[*]Please, please, read some documentation. Start at [http://latex.silmaril.ie/formattinginformation](http://latex.silmaril.ie/formattinginformation) (warning: bias: I wrote it)
[*]"The Internet" (by which I assume you mean Google) is The Wrong Place  to look for arbitrary beginner help on LaTeX. Google simply isn't sensitive enough to understand what is being sought.
[*] The Right Place is the Usenet newsgroup comp.text.tex, available from any decent ISP via any decent mailer/newsreader. Google also provides access at [http://groups.google.com](http://groups.google.com) but the interface is terrible.
[/LIST]

> **VCoolio said:**
> But it is possible. A friend of mine accomplished the almost impossible task of putting one special unicode character in latex ( << sarcasm ) by using lyx and then checking the .tex file.

Your sarcasm is understandable, but most of these characters have names or numbers, so use them instead. Look at the LaTeX Symbols List at [http://www.ctan.org/tex-archive/info/symbols/comprehensive/](http://www.ctan.org/tex-archive/info/symbols/comprehensive/) (available in A4 and Letter).

Best of all, use a proper Unicode editor (see below), then you can just type the character using the facilities provided. Don't try to do a task using the wrong tools.

> **VCoolio said:**
> Seems like \usepackage{amssymb} is the solution in this particular case, although I can't understand why I didn't read about this in a day long googling around.

You simply won't find that depth of information in a Google search unless you already know how to look for it. Google just isn't clever enough for that yet.

> **VCoolio said:**
> Anyway, biggest lesson is to take a break if something doesn't work and try again next day. Also latex really seems like an opportunity: gedit now has more features for me than any office suite.

gedit is a very poor tool for LaTeX. Use Kile or Emacs.

---

### Post by VCoolio on 2009-11-29
> **frisket said:**
> [LIST=1]
[*]Please, please, read some documentation. Start at [http://latex.silmaril.ie/formattinginformation](http://latex.silmaril.ie/formattinginformation) (warning: bias: I wrote it)
[*]"The Internet" (by which I assume you mean Google) is The Wrong Place  to look for arbitrary beginner help on LaTeX. Google simply isn't sensitive enough to understand what is being sought.
[*] The Right Place is the Usenet newsgroup comp.text.tex, available from any decent ISP via any decent mailer/newsreader. Google also provides access at [http://groups.google.com](http://groups.google.com) but the interface is terrible.
[/LIST]

Your sarcasm is understandable, but most of these characters have names or numbers, so use them instead. Look at the LaTeX Symbols List at [http://www.ctan.org/tex-archive/info/symbols/comprehensive/](http://www.ctan.org/tex-archive/info/symbols/comprehensive/) (available in A4 and Letter).

Now here is a comment that is helpful! Thanks. Only if I search for my sign (I searched for \mathfrak because that was in the error when I used it in gedit) I am pointed to the package eufrak (page 68 of the symbols list), while I got it with amssymb. They both work, so I'll stick with eufrak.
Sorry for the sarcasm and stuff, but I was trying to learn latex (with some manuals btw) and then came up with this very specific request. So I thought let's google it, but that resulted in a whole day of frustration... I get something like "just do \char"unicode " or "just do \whatever-char-name " and then it just doesn't work and it appears I also need a \usepackage no one mentioned. Now what you did is far more useful.

> 
Best of all, use a proper Unicode editor (see below), then you can just type the character using the facilities provided. Don't try to do a task using the wrong tools.

You simply won't find that depth of information in a Google search unless you already know how to look for it. Google just isn't clever enough for that yet.

gedit is a very poor tool for LaTeX. Use Kile or Emacs.
Hmm, I'm already learning latex, I'm not up to learning how to use a difficult editor also. Besides, gedit has syntax highlighting, autocomplete, embedded preview, can use bibtex, has buttons for listing, numerating, structuring, can open the file with an external pdfeditor, what more do I need? I can also use unicode in it: the papyrus sign shows perfectly.

---

### Post by samden on 2009-11-29
I use LaTeX heavily (have written an entire PhD thesis among others) and use gedit exclusively for it (on my Ubuntu machines anyway). Sure Emacs would be better - if I had the time to learn it. And one day I probably will. But gedit is a great program, just use it if it works for you.

Check out the Latex Community forum as well for future questions. You might get the answer from us, but that's another option.
[http://www.latex-community.org/forum/](http://www.latex-community.org/forum/)

---

