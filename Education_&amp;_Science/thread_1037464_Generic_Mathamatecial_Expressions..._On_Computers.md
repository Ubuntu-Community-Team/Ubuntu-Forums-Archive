---
title: "Generic Mathamatecial Expressions... On Computers"
date: 2009-01-11
forum: Education &amp; Science
---

### Post by Pyro.699 on 2009-01-11
Hello,

Im interested in programming several different types of programs that can preform very complex calculations but have ran into the problem of a simple way to create an expression for different types of calculations. To put it simply taking the calculation like:
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]http://upload.wikimedia.org/math/4/f/0/4f0feb251d1976d70f645ee00caa089e.png[/IMG]

could be written as:

**\sum_{k = 0}^{n} \frac{16^{n-k} \mod 8k+1}{8k+1} + \sum_{k = n + 1}^{\infty} \frac{16^{n-k}}{8k+1}**

(Calculation for extracting 16bit values of PI)

My question is where i can find a documentation on this kind of expression (like if i had my own expression and wanted to change it into that kind of format).

Thanks
~Cody Woolaver

---

### Post by ProgramErgoSum on 2009-01-11
I don't have a direct answer. But, here is a thought...

How would the mathematical expression be input to your program ? 

Consider Open Office suite's Formula s/w. You can build the expression you have written above and save it into one of the popular formats (latex, [MathML]("http://en.wikipedia.org/wiki/MathML"), etc.). Once saved, you could then parse it in the way that particular format is document.

---

### Post by Pyro.699 on 2009-01-11
Thanks, after reading that document i found that the syntax is called [LaTeX](http://en.wikipedia.org/wiki/LaTeX)

---

