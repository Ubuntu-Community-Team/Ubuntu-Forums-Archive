---
title: "LaTeX Beamer coloured box"
date: 2009-08-17
forum: Education &amp; Science
---

### Post by samden on 2009-08-17
I am trying to place a plain colour box with rounded corners behind my tables. However nothing I do seems to give me any colour behind them at all. The code I am trying to use is:
```
\begin{beamercolorbox}[wd=90mm,rounded=true,center]{rose}
\begin{tabular}{lccc} 
\underline{My fancy table:}  \\
Stocking rate & 1 & 2  & 3  \\ 
No.~of urine patches & 1000 & 3000 & 5000 \\
Area coverage by urine & 20 \% & 20 \% & 22 \% \\  
\end{tabular}
\end{beamercolorbox}
```
This however only gives me black text on a white background. The rose theme should have a pale blue background here I would have thought, but whatever theme I try I still have no background.

I'm bound to be doing one little simple thing wrong, but I can't figure out what it is!

---

### Post by meborc on 2009-08-18
EDIT: sorry.. .misread your post

---

