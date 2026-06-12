---
title: "latex help"
date: 2009-06-20
forum: Education &amp; Science
---

### Post by mthalis on 2009-06-20
Can any tell how to code this table using latex

---

### Post by ad_267 on 2009-06-21
See here: [http://en.wikibooks.org/wiki/LaTeX/Tables](http://en.wikibooks.org/wiki/LaTeX/Tables)

---

### Post by jimv on 2009-06-21
Have you tried an editor like Lyx?

[http://www.lyx.org/](http://www.lyx.org/)

---

### Post by mthalis on 2009-06-21
I found it

\begin{center}
\begin{tabular}{|l|c|c|c|c|} \hline
\multirow{2}{*}{Visit share by OS } & \multicolumn{2}{c}{2008} & \multicolumn{2}{|c|}{2009} \\\cline{2-5}
  & November &	December &	January &	February \\\hline
Microsoft &	93.90\% & 93.91\% & 93.70\% &	93.82\% \\\hline
Windows XP & 65.78\% & 64.48\% & 63.06\% & 62.18\% \\\hline
Windows Vista & 24.93\%	& 26.63\% &	27.89\% &	28.90\% \\\hline
Windows 2000 & 1.35\% & 1.19\% &	1.15\% &	1.20\% \\\hline
Linux &	1.19\%	&1.17\%&	1.21\%&	1.24\% \\\hline
\end{tabular}
\end{center}

---

