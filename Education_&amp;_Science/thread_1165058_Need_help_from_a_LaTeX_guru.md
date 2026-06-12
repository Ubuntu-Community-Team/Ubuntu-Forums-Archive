---
title: "Need help from a LaTeX guru"
date: 2009-05-20
forum: Education &amp; Science
---

### Post by Ruffed Grouse on 2009-05-20
Hi,  Are there any \latex gurus here?

If so can you provide me with some pointers to make
the following table.  As far as I can tell, it requires 
multicolumns within multirows within multicolumns,
but I can't figure out how to code it.

------------------------------------
|***|***|*******|*******|
|***|***|-----------------------
|***|***|***|***|***|***|
------------------------------------
|***|***|***|***|***|***|
------------------------------------

Unfortunately, I could not make this diagram as clear as I wanted, because when I used spaces, continuous stretches of space would collapse in the preview.  Here any ---- or | represent breaks between cells.

Perhaps a clearer way to describe it would be to think of the table without any merged cells as a 6 colums by 3 row table.  I want to make the following merges:
column 1 row 1 with column 1 row 2
column 2 row 1 with column 2 row 2
column 3 row 1 with column 4 row 1
column 5 row 1 with column 6 row 1

Actually the table I need to make replicates this pattern a little more, but if someone can show me how to code this I'll be able to scale it up.

Thanks very much, 

Michael

<>< <>< <>< <><

---

### Post by samden on 2009-05-20
I'll presume you want all columns centered for now, I'm sure you know how to change that:

Place \usepackage{multirow} in your preamble.

\begin{tabular}{cccccc}
\multirow{2}{*}{text} & \multirow{2}{*}{text} & \multicolumn{2}{c}{text} & \multicolumn{2}{c}{text} \\
 &  & text & text & text & text \\
text & text & text & text & text & text \\
\end{tabular}

The key commands are 
\multicolumn{number of columns}{alignment}{text in cell}
\multirow{number of rows}{alignment}{text in cell}

---

### Post by samden on 2009-05-20
Good example of a table with both multirow and multicolumn in it here:
[http://andrewjpage.com/index.php?/archives/43-Multirow-and-multicolumn-spanning-with-latex-tables.html](http://andrewjpage.com/index.php?/archives/43-Multirow-and-multicolumn-spanning-with-latex-tables.html)

---

### Post by Ruffed Grouse on 2009-05-21
Thanks very much - tried and tried but just couldn't get it right.

<><

---

### Post by samden on 2009-05-21
No worries, hope it works well for you.

---

