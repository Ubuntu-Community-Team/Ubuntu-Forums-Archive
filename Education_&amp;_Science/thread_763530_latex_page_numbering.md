---
title: "latex page numbering"
date: 2008-04-23
forum: Education &amp; Science
---

### Post by dhap on 2008-04-23
I used alphabatical, roman and arabic page numbering in my thesis. The roman and arabic page numbering surprisingly starts from a left side page (i.e., an even page). I mean, page 2 of the document is called roman-i and page 4 is called arabic-1.
The beginning of thesis looks like this (document class is report). 

\begin{document}
\pagenumbering{alph}
\input{Title}
%To add a blank page without header or footer
\newpage
\thispagestyle{empty}
\mbox{}
\pagenumbering{roman}
\include{abstract}  
\tableofcontents
\listoffigures
\cleardoublepage    
\pagenumbering{arabic}
\include{Introduction}
.
.
.
\include{conclusion}
\end{document}

---

### Post by xadder on 2008-04-24
I can't remember the details of why, but try setting the numbering style after the new sections start, e.g.:

```

\documentclass[]{report}
\begin{document}
\pagenumbering{alph}
%\input{Title}
TITLE IS HERE, ALPHABETICAL
%To add a blank page without header or footer
\newpage
\thispagestyle{empty}
\mbox{}
\include{abstract}
%
ABSCTRACT SHOULD HAVE ROMAN
\pagenumbering{roman}
\tableofcontents
\listoffigures
\cleardoublepage
\include{Introduction}
\pagenumbering{arabic}

TEXT IS HERE, ARABIC

BLA BLA
%\include{conclusion}
\end{document}

```

---

### Post by dhap on 2008-04-25
Thanks, I was playing around my code and found that this one works:


\documentclass[a4paper, 12pt]{book}
\begin{document}

\pagenumbering{alph}
\input{Title}
\cleardoublepage
\thispagestyle{empty}


\pagenumbering{roman}
\include{abstract}  
\tableofcontents
\listoffigures
\cleardoublepage
    

\pagenumbering{arabic}
\include{Introduction}

BLAH BLAH

\end{document}

---

