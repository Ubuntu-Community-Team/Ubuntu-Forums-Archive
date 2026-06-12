---
title: "export to pdf in Lyx"
date: 2007-01-26
forum: Education &amp; Science
---

### Post by fifafrazer on 2007-01-26
When I export my lyx documents to pdf, the letters look unneat. See this pic:

[[IMG]http://img260.imageshack.us/img260/2334/lyxog9.th.png[/IMG]](http://img260.imageshack.us/my.php?image=lyxog9.png)

The first line is how the lyx-produced pdf looks like with a 3200 % zoom, and the other line is how the letters should look like. Text typed in mathmode looks like it is supposed to. How can I fix this?

and also:
How can I have the same header and footer on all pages?
I've used the following in the preamble: \rfoot{page \thepage\ of \pageref{lastpage}} but on the first page it says  1   in the center footer, and the right footer is empty.

---

### Post by fifafrazer on 2007-01-26
Oh.. The unneat text issue was solved by selecting another font..

---

### Post by slaanco on 2007-01-26
i'm not really sure, but lyx may use pdflatex which gives different result as latex, in means of used font, try to make .dvi file, and then use dvipdfm .

---

