---
title: "gnuplot + commandline"
date: 2009-02-28
forum: Education &amp; Science
---

### Post by babyboss on 2009-02-28
Hello, I only have installed commandline, and no x windows at all. Am I ample to use gnuplot program under commandline to plot graph at all?
Thank you

---

### Post by dikarus on 2009-02-28
yes, you can! just select a proper terminal and output file:

set term postscript eps enhanced color
set output "my_graph.eps"

and the plot will be in eps format and redirected to my_graph.eps

of course you can select different terminals, like pdf, png, etc.

---

