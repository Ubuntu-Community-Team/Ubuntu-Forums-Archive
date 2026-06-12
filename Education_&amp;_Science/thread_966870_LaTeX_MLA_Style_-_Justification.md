---
title: "LaTeX MLA Style - Justification"
date: 2008-11-01
forum: Education &amp; Science
---

### Post by dmbrown00 on 2008-11-01
I have a LaTeX document using the mla package for MLA style, but want it to still justify the text.  The mla package seems to force everything to be flushleft.

---

### Post by Stefan_K on 2008-11-02
Hi,

if you mean the mla package contained in TeX Live 2007 you could use this redefinition in your preamble:
```
\renewenvironment{mla}[6]{\newcommand{\lastname}{#2}
\fancyhead[RO]{\lastname\ \thepage} {\raggedright #1\ #2 \\  #3 \\ #4 \\ #5 \\}
{\centering #6 \\} \frenchspacing\setlength{\parindent}{.5in}}{\newpage}
```
Stefan

---

