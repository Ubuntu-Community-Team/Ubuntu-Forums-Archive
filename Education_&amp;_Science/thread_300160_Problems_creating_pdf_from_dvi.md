---
title: "Problems creating pdf from dvi"
date: 2006-11-15
forum: Education &amp; Science
---

### Post by jmercer on 2006-11-15
I recently upgraded to Edgy and now I cannot turn my MSc Thesis into a pdf. Here is an example of the failure on a very simple tex document. In this case, dvipdf would work, but it doesn't on my thesis. I'm writting with Kile and it uses dvipdfm to create the pdf. 

Any ideas? I'm rather frantic. 

```

jason@isaac Documents $ cat test.tex
\documentclass[a4paper,10pt]{article}

\begin{document}
blah blah
\end{document}

jason@isaac Documents $ latex test.tex
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./test.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo)) (./test.aux) [1]
(./test.aux) )
Output written on test.dvi (1 page, 216 bytes).
Transcript written on test.log.
jason@isaac Documents $ dvipdfm test.dvi

test.dvi -> test.pdf
[1]
pdf_ref_obj:  Called with already released object{0}
Fatal Error


Output file removed.
jason@isaac Documents $     

```

---

### Post by Steveire on 2006-11-15
There was a post here recently about that. I think the guy used dvipdf instead of dvipdfm. Why can't you use dvipdf on your thesis? Another idea would be the dvips > ps2pdf route. Just click those buttons in Kile.

---

### Post by jmercer on 2006-11-15
If I use dvipdf on my thesis, I get this:

```

jason@isaac thesis $ dvipdf Thesis.dvi
ERROR: /syntaxerror in --%ztokenexec_continue--
Operand stack:
   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1120/1686(ro)(G)--   --dict:0/20(G)--   --dict:82/200(L)--   --dict:154/300(L)--   --dict:43/200(L)--
Current allocation mode is local
ESP Ghostscript 815.02: Unrecoverable error, exit code 1
jason@isaac thesis $

```

I can copy my entire thesis project dir to an old redhat server here and run dvipdfm on it and it compiles fine, but what a pain that is.

I tried the ps2pdf route, I can generate a ps file, but converting to pdf yields: 

```

jason@isaac thesis $ ps2pdf Thesis.ps
ERROR: /syntaxerror in --%ztokenexec_continue--
Operand stack:
   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1121/1686(ro)(G)--   --dict:0/20(G)--   --dict:82/200(L)--   --dict:154/300(L)--   --dict:43/200(L)--
Current allocation mode is local
Current file position is 2602202
ESP Ghostscript 815.02: Unrecoverable error, exit code 1
jason@isaac thesis $   

```

---

### Post by jmercer on 2006-11-15
I just discovered that the .ps file that I get from dvips cannot be viewed with gv. It fails with the errors above on pages with images, pngs in this case. Pages with embedded .eps files work fine.

---

### Post by Campitor on 2006-11-15
> **jmercer said:**
> I just discovered that the .ps file that I get from dvips cannot be viewed with gv. It fails with the errors above on pages with images, pngs in this case. Pages with embedded .eps files work fine.
Have you tryed saving the *.tex file and doing pdflatex?
Also, have all the required packages installed? Go to synaptic and
search for TeX or LaTeX and see if all the necessary packages
are installed.

---

### Post by jmercer on 2006-11-15
pdflatex errors on the first graphics file (happens to be an eps). 

If I skip that error, it gets confused on other pngs, some of my filenames have decimals in them (SKEW_11.25.png and whatnot) and it says it doesn't know what filetype .25.png is. 

The output has warnings about not knowing what bb is and it shows as many of my images have insane bounding boxes and stretch off the page. Some are just black boxes. 

It is creating a pdf, so that's good. It would be nice if I could figure out what's wrong with the way I used to do things. 

Edit: Seems the bounding boxes are my mistake. 

I guess I'll convert my .eps to a png and change my filenames and see if I can do something about these bounding boxes.

---

### Post by neoflight on 2006-11-15
its seems there is problem with pdf stuff in the latex installation you are using.  what installation are you using? 

did you try texlive from universe repos for edgy? 

i use dvipdfm btw.

---

### Post by jmercer on 2006-11-15
I had tetex since kile pulls that in. I'm now switching over to texlive...

OK, tetex is gone. texlive is installed and I have the same errors.

On a whim, I installed dvipdfmx and it can do the conversion.

---

### Post by Miguel on 2006-11-15
Hi guys,

Neither pdflatex nor pfetex support eps images (nor ps files for what is worth). AFAIK, it's because those images have additional embedded info. However, you might convert them to pdf using (of course) ps2pdf, and these should work. Oh! pdflatex (or pdfetex or whatever the default in teTeX 3 is) should support png's or at least jpg's.

A PhD student writing something that he shouldn't,

Miguel

---

### Post by J77 on 2007-12-05
I'm having the same problem -- it's with the ghostscript. Loads of packages rely on it, like ps2pdf, xfig and ggv, but when I updated my gs recently everything broke.

I have no time to try to fix this now -- if anyone knows how that would be great -- for now, I'm having to work between desktop and laptop :(

---

### Post by Miguel on 2007-12-05
Since the migration to TeX live, I've been happily using dvipdfmx, where the **mx** part is important to make the eps figures go nicely.

---

### Post by J77 on 2008-02-08
This wasn't solved, was it...?

Anyway, solution  is that fonts aren't in the gs path.

There's a nice gs group explanation somewhere...

Bottom line is, do gs -h to see the paths and find . -name '*.pfb' to find fonts. If font dirs aren't in path, add them -- I add them all because different apps seem to use diff font sets with gs...

You can add them in eg .bashrc as path GS_LIB='blah : blah : blah'

This works for stuff like ps2pdf, ggv, xfig...

:guitar:

---

