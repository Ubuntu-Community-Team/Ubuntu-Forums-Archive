---
title: "Printing exactly the selected part of a table in OpenOffice"
date: 2007-04-22
forum: Education &amp; Science
---

### Post by der_vegi on 2007-04-22
Hi!

I've got a problem: I have big tables that I want to insert into my latex file. Right now I am doing it like this: I work with the table in Oocalc, select the part i want in my latex file and print the selection as ps-file. The problem is, that during printig, a whole page is built around my selected part of the table, so the output ps file is way too big. I have to edit it in gimp first, to cut away the blank part of the page.

So is there a possibility to print the selected part of the table into a file so that the size of the ps file is just as big as the selected part?

Thanks for the help!

---

### Post by frisket on 2007-04-23
Why are you trying to include a picture of the table instead of making the table in LaTeX?
LaTeX makes much better tables than Oocalc.  If you want to maintain the data in Oocalc, then export the table as CSV and use the csvtools LaTeX package to read it into a table.

To answer your question, yes, you can crop away part of an EPS image in the \includegraphics command (read about crop and viewport), but you'll get a much better quality table if you do it in LaTeX than in Oocalc. If the table is bigger than one page, use the longtable package.

---

### Post by NikoC on 2007-04-25
What you could also do is export the table as a text file and have the column separations defined with an '&', this way you only have to define your tabular environment in Latex and you can copy all the colums directly from the  text-file.

---

### Post by der_vegi on 2007-05-13
thanks very much! exporting the table as cvs worked really well.

---

