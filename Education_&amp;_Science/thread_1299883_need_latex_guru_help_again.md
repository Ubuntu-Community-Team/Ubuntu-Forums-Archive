---
title: "need latex guru help again"
date: 2009-10-24
forum: Education &amp; Science
---

### Post by Ruffed Grouse on 2009-10-24
Hi,

I have eps files that I generated in R.  I am trying to include it in a manuscript.  Everything works fine with all other images (all eps) except one.  It gets rotated and squished without me asking for it.

The file in question was generated with the following R code (edit: note the smiley face is something automatic, not a relevant aspect of the code!):

postscript("/home/michael/Desktop/mmPowerPlot.eps",width=8,height=8)
persp(x=testp,y=testa,z=likelihoodRatios,theta=40,phi=25,xlab="Mutant allele frequency",ylab="Allelic substitution effect",zlab="Probability of significant test")
dev.off()

and the relevant bit of latex is:

\begin{figure}
      \includegraphics{mmPowerPlot.eps}
     \caption{test}
     \label{fig:mixture}
\end{figure}

I only have the problem with this one file.  It is the only '3D-like' perspective plot of the bunch, though, and I suspect it has something to do with that.

RG

<><

---

### Post by Chronon on 2009-10-25
What's the compilation process?  Is the problem in PDF and PS or only in DVI?  I have some images that appear broken in DVI (something wrong with previews, I guess), but dvipdf, etc. produce fine results for output.

---

### Post by hubie on 2009-10-25
Just for clarification, are the figures that don't give you a problem also generated with R?  If so, could you give an example of the script that generated them?

---

### Post by XCan on 2009-10-25
How does it look if you simply open it with evince? Does it get rotated?

---

