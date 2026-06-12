---
title: "No image in pdflatex output"
date: 2009-01-29
forum: Education &amp; Science
---

### Post by brunods on 2009-01-29
So, I'm having the weirdest problem:

I have a latex script and I have a personalized title page. And I tried to put an image in it.
So I wrote:

\usepackage[pdftex]{graphix}
...
\includegraphics[scale=1}{image.png}


when I run pdflatex myfile.tex id doesn't give me any warnings or errors. But when I run evince myfile.pdf The is just a bounding box with no picture in it and a big caption saying "image.png"

Anyone has got any Idea what's going on?

---

### Post by mister_pink on 2009-01-29
Easiest way to get help with latex is to make a minimal example: [http://theoval.sys.uea.ac.uk/~nlct/latex/minexample/](http://theoval.sys.uea.ac.uk/~nlct/latex/minexample/)

However here the problem seems to be mixed brackets:
\includegraphics[scale=1**}**{image.png}

---

### Post by brunods on 2009-01-29
OOPS.

Sorry you all, I realized I was in draft mode... had forgotten all about it.

but I leave the tip: if you are in draft mode picture will not show!


cheers

---

