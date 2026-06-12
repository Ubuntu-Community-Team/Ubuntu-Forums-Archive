---
title: "Merging PDFs in a LaTeX document"
date: 2009-12-01
forum: Education &amp; Science
---

### Post by kbaumen on 2009-12-01
Hi.

I am trying to make aPDF document out of a bunch of ppt presentations. I used Open Office to export them as PDF. Now I want to put all the PDFs in a single PDF file and am trying to do that with LaTeX. However, the \includegraphics{1.pdf} gives only the first slide of the presentation. How could I make all of the pages from each PDF appear in the final document?

Here's my code, in case that might help.

 p, li { white-space: pre-wrap; }  ```

\documentclass[a4]{article}
 \usepackage{graphicx}
 \title{ME101 Heat & Flow Lecture Notes}
 \begin{document}
 \maketitle
 \includegraphics[scale=0.5]{1.pdf} \\
 \includegraphics[scale=0.5]{2.pdf} \\
 \includegraphics[scale=0.5]{3.pdf} \\
 \includegraphics[scale=0.5]{4a.pdf} \\
 \includegraphics[scale=0.5]{4b.pdf} \\
 \includegraphics[scale=0.5]{5a.pdf} \\
 \includegraphics[scale=0.5]{5b.pdf} \\
 \includegraphics[scale=0.5]{5c.pdf} 
 \includegraphics[scale=0.5]{5d.pdf} 
 \includegraphics[scale=0.5]{6.pdf} 
 \includegraphics[scale=0.5]{6a.pdf} 
 \includegraphics[scale=0.5]{7.pdf} 
 \includegraphics[scale=0.5]{8.pdf} 
 \includegraphics[scale=0.5]{9.pdf} 
 \includegraphics[scale=0.5]{10.pdf} 
 \includegraphics[scale=0.5]{11.pdf} 
 \includegraphics[scale=0.5]{12.pdf} 
 \includegraphics[scale=0.5]{13.pdf} 
 \includegraphics[scale=0.5]{14.pdf} 
 \includegraphics[scale=0.5]{15.pdf} 
 \includegraphics[scale=0.5]{16.pdf} 
 \end{document}

```

---

### Post by cholericfun on 2009-12-01
this is off some thread from this forum which i'm not bothered to find now:

using gs - not latex

```
gs -q -sPAPERSIZE=letter -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=out.pdf in1.pdf in2.pdf in3.pdf ...
```

---

### Post by favilac on 2009-12-01
Much easier solution.

Use pdfjoin. It's included in the pdfjam package.

---

### Post by Dougie187 on 2009-12-01
> **favilac said:**
> Much easier solution.

Use pdfjoin. It's included in the pdfjam package.

These only work if you don't mind not having a title page. Though, you could make the title page with latex, and then use pdfjoin to merge all of them together.

I have never tried what you are doing, but I would assume you need pdflatex for including pdf files. Also, another method would be to convert all of your pdfs to eps files and then include those.

---

### Post by kbaumen on 2009-12-01
I solved the problem by finding a program called pdfsam. Thanks for any help anyways.

---

### Post by samden on 2009-12-01
For anyone else with the same issue, try pdftk, that's what I use for similar work. LaTeX is a very complicated way of doing it.

---

### Post by jarlz0r on 2009-12-02
Put this into your header:
```

\usepackage{pdfpages}
\pdfminorversion=6 % removes some warnings

```

Use 
```

\includepdf{file}

```
to include the pdf-files. If you wish for several logical pages per page, the option "nup" is useful -- or you could just tell your reader to print several pages per sheet. See [the pdfpages reference](http://www.ctan.org/tex-archive/macros/latex/contrib/pdfpages/pdfpages.pdf) for more info!

---

