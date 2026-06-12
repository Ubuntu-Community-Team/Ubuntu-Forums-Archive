---
title: "LaTeX: Headings containing terms from description enviroment"
date: 2009-03-10
forum: Education &amp; Science
---

### Post by Repabil on 2009-03-10
Hey

I'm trying to typeset a dictionary in LaTeX. I've got a whole lot of terms definid within a description environment. What I would like is the heading for every page to contain the first and the last term on the page and also an index refering to each page by its heading. I've been reading [the fancyhdr manual]("http://www.ctan.org/get/macros/latex/contrib/fancyhdr/fancyhdr.pdf") but I can't seem to find any solution there. Would appreciate any advice.

---

### Post by ondra.cifka on 2010-05-19
Hi, I'm interested in this, too. Did you get any solution?

---

### Post by Repabil on 2010-05-20
Hey

I'm afraid I never solved it. I tried to use something like```
\usepackage{fancyhdr,ifthen}

\renewcommand{\headrulewidth}{0pt}
\renewcommand{\sectionmark}[1]{}

\pagestyle{fancy}
\fancyhf{}
\fancyhead[C]{\mymarks}
\fancyfoot[C]{\thepage}

\newcommand{\mymarks}{
  \ifthenelse{\equal{\leftmark}{\rightmark}}
    {\textbf{\rightmark}} % if equal
    {\textbf{\rightmark}--\textbf{\leftmark}}} % if not equal
```together with a command that typeset every term *and* its name in a mark:```
\newcommand{\word}[2]{\item[#1]\markboth{#1}{#1}#2}
```But there was always somewhere in the document where the wrong words showed in the heading.

Would appreciate a reply if you manage to solve it.

Good luck!

---

