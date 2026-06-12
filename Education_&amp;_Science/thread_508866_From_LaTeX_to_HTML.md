---
title: "From LaTeX to HTML"
date: 2007-07-24
forum: Education &amp; Science
---

### Post by Fingolfin on 2007-07-24
How does one convert a LaTeX document into HTML using KILE (and teTeX)?
The toolbar icon LaTeXtoHTML begins an action which ends with the message "Exit status 127". Neither the TeXmaker's menu option "Convert to HTML" works.
Probably a particular conversion utility needs to be installed and linked to the icon on the KILE toolbar. Or is it something else that is missing?

---

### Post by xadder on 2007-07-25
Sorry, can't help with using kile. Do you have latex2html installed though? Try it from the command line.

---

### Post by Fingolfin on 2007-07-25
Yes, latex2html was the missing link. I thought that the utility for this conversion came as part of the teTeX applications package.
Once installed witj Synaptic, the latex-to-html icons in KILE and TeXmaker recognized it and the job is now done easily.
Thank you. :-)

---

### Post by frisket on 2007-08-13
> **Fingolfin said:**
> How does one convert a LaTeX document into HTML using KILE (and teTeX)?

One doesn't. Kile is an editor, not a converter.

Use TeX4ht, which is much better than LaTeXtoHTML (IMHO).

---

### Post by euler_fan on 2007-08-13
you might also switch to TeXlive as the word on the street (at least in this forum) is that tetex is no longer being maintained or else maintained very slowly.

I have found that the TeXLive packages in the repos contain almost everything one would want.

---

### Post by Fingolfin on 2007-09-17
Does this TeX distribution use the same collection of compilers (like pdfetex for example) as teTeX and how does it differ from teTeX?

---

