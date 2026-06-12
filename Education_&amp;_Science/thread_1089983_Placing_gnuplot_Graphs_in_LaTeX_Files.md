---
title: "Placing gnuplot Graphs in LaTeX Files"
date: 2009-03-07
forum: Education &amp; Science
---

### Post by Jaded Misanthrope on 2009-03-07
Some work I am doing would be vastly clearer if I were able to insert images into the LaTeX file (more specifically, graphs from gnuplot). I've tried Googling the matter, but to no avail. What image format would be best to use for the graph, how would I have gnuplot output a graph in this format and how would I embed the resulting file into the LaTeX file?

---

### Post by favilac on 2009-03-07
Gnuplot can output graphics to the .eps format (encapsulated postcript).

 You can use it directly in LaTeX, unless you use pdflatex to create the document.

 If this is the case, use epstopdf to convert the .eps graph to an .pdf file.

 With the .pdf graph and the pdflatex you can insert it like this:

\begin{figure}[htpb]
\begin{center}
\includegraphics[scale=1]{graph-file}
\end{center}
\caption{some text here}
\label{Another text here}
\end{figure}

---

### Post by Dougie187 on 2009-03-07
AFAIK You cannot include eps files if you use pdflatex to create your pdf from your latex files, however if you use pdflatex you can include png files. Thats one choice you will have to make..

Eps -> Latex -> Dvipdf
Png -> Pdflatex

Now inside gnuplot you have to tell it to output to whatever format you want. I usually go with eps (they tend to look better when scaling, for me at least). This is the command I give.

```
set term pos eps color enhanced defaultplex "Helvetica" 26
```
After this you would set your output file like this
```
set output 'Graph.eps'
```
And then you can go ahead and plot as normal. Now instead of being able to see the plot, it will just create a file for you called Graph.eps. You can view this is evince if you want to see what it looks like.

Also, there is a terminal option called epslatex, using this gnuplot will create an eps of the graph, as well as a latex file that you can just include (or copy the contents of) to put the graph into a document.

---

### Post by Jaded Misanthrope on 2009-03-08
Brilliant, that got the graphs in. Is it possible to have the graph in the .eps file centred, though? As it is, the graph is a fair bit off-centre, which looks a bit odd in the .dvi.

---

### Post by utgodmode on 2009-05-14
Thanks favi that worked like a charm.

---

