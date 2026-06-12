---
title: "LaTeX - won't import graphics or bibliography"
date: 2009-01-17
forum: General Help
---

### Post by I[AM]SMRT on 2009-01-17
I have my texfile written up in texmaker:

[http://www.ugrad.physics.mcgill.ca/resources/latex/template/template.tex](http://www.ugrad.physics.mcgill.ca/resources/latex/template/template.tex)

The relevant lines being:

```
\begin{figure}[H]
\begin{center}
\includegraphics[scale=0.65]{pendulum.eps}
\end{center}
\caption{Variation of period of a pendulum as a function of length.}
\label{FIG-PEND}
\end{figure}
```

```
\bibliographystyle{unsrt}	% Order by citation
\bibliography{report}
```

For some reason, it seems like the graphics nor the bibliography are being imported. The .eps files and the .bib file are all in the same directory as the .tex file. I definitely have the graphicx package and I'm pretty sure I have the unsrt package. I've been looking at this for the past hour or so and haven't gotten anywhere =/.

---

