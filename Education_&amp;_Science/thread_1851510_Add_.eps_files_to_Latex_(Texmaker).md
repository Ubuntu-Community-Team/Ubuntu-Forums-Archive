---
title: "Add .eps files to Latex (Texmaker)"
date: 2011-09-28
forum: Education &amp; Science
---

### Post by anohs on 2011-09-28
I wanted to add .eps file to my latex document. But which option to use to compile my code??  I mean the option on top (latex,pdflatex etc)?? and how can i view ps/pdf output??

---

### Post by euler_fan on 2011-09-28
> **anohs said:**
> I wanted to add .eps file to my latex document. But which option to use to compile my code??  I mean the option on top (latex,pdflatex etc)?? and how can i view ps/pdf output??

The ```
\includegraphics
``` command is what you are looking for. [LaTeX Wikibook]("http://en.wikibooks.org/wiki/LaTeX") is an excellent all-around reference for how to use this function.

The other issue is that EPS works best with dvi output. The eps2pdf package provides functionality if you want PDF output. I have found this to be tricky to get right, ergo I prefer to make my origional graphics in EPS and then convert them to JPEG using GIMP once I know how big I will need them in the document.

---

### Post by jeneverboy on 2011-09-29
I use only .eps in my latex with texmaker. In texmaker you can LaTeX (F2) dvi2ps (F4) and ps2pdf (F8 ) and you have the best looking pictures in your document.

.eps is vector so it doen't get any better :).

bye

---

### Post by anohs on 2011-09-29
Thanks a lot.

---

### Post by FreeTheBee on 2011-10-01
I would recommend using pdf2latex with eps2pdf to convert the images on the fly to pdf. You might need to add --shell-escape to the compile command to get it to work. 
For me, the dvi --> ps --> pdf route sometimes led to problems with the final layout, the margins in particular. Also microtype does not fully function when compiling to dvi.

---

