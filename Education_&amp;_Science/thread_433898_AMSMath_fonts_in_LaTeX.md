---
title: "AMSMath fonts in LaTeX"
date: 2007-05-05
forum: Education &amp; Science
---

### Post by dschmier on 2007-05-05
I've been trying to use the "amsmath" package but I keep running into an error involving fonts.  I think the package is correctly installed but when I try to compile my document I get the error: 

```
Font OMX/cmex/m/n/7=cmex7 not loadable: Metric (TFM) file not found
```

This is actually addressed in the documentation for the package but there they only say that I should try to get the fonts from wherever I got LaTeX, or otherwise I can download them from CTAN.  I've downloaded the fonts from CTAN (they're available either as Metafont source files or in PostScript Type 1 format) but I have no idea what to do with them or where to put them.  

Has anyone else had this problem or have any ideas what I should do with these font files?  I would be willing to just do a fresh tex install if I thought that would help.  Any ideas?  Thanks.

---

### Post by kleeman on 2007-05-05
This may be useful:

[http://www.tex.ac.uk/cgi-bin/texfaq2html](http://www.tex.ac.uk/cgi-bin/texfaq2html)

Personally I would install texlive-full from the universe repo and get a full latex install which I believe has the fonts you need. The installation will set everything up for you......

---

### Post by dschmier on 2007-05-09
Thanks, that definitely took care of the problem.  Now I shouldn't ever be missing a package.

---

