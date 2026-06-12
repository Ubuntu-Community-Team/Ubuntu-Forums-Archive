---
title: "HA-prosper"
date: 2007-11-16
forum: Education &amp; Science
---

### Post by vcadavez on 2007-11-16
Hello,
I'm trying to use HA-prosper on Kile!
I get this error! Somebody can help me?

[PDFLaTeX] prosper.tex => prosper.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./semcolor.sty:43:File `pstricks.sty' not found. \def
[PDFLaTeX] 1 error, 0 warnings, 0 badboxes

Thanks

---

### Post by schristo on 2008-01-31
Although this is quite an old thread, I just came upon it. The answer to your problem is simple: HA-Prosper does not work with PDFLaTeX. You need to use the traditional route of tex->dvi->ps->pdf, since HA-Prosper uses PStricks to place some of the content in the page.

This also means that you should not use PDF figures in your presentation but EPS, since LaTeX cannot use PDF figures directly. You can use pdftoeps in order to convert your figures.

---

### Post by dikarus on 2009-02-28
Mmmmh, is there any particular reason for that?

I mean, it's said that prosper can't work with pdflatex. Well, it's now a few months that I'm writing my slides using **pdflatex + prosper**! 
Yes, I always get a relatively long list of

Non-PDF special ignored!

but they have no effect at all on the result and they do not cause the compilation to stop. So, who cares that they are there ...;)

Today I discovered HA-prosper, but the same 'trick' doesn't work. Compilation stops immediately outputting:

! Undefined control sequence.
<recently read> \c@lor@to@ps

l.10 \end{slide}

Clearly indicating a problem with PSTricks. Does anybody has any idea how to make it working the same it 'works' with prosper?

---

