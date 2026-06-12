---
title: "How to align around equal sign using OOoLaTeX"
date: 2009-03-14
forum: Education &amp; Science
---

### Post by amylase on 2009-03-14
Hi

I am using OpenOffice 2.4 with OOoLaTeX plug-in on Ubuntu 8.10

How do I write an array of mathematical equations that align along equal sign? For example I'd like the following to have equal signs all nicely aligned such that E & F are directly below C & D and not like the way it's shown here - 
A + B = C + D
      = E + F
      = 3

I quickly searched online and this kind of code was suggested:
```
  \usepackage{amsmath}
   \begin{eqnarray} 
   q(v) & =&  q(v_{1},...,v_{d-1}) \\
   & = &  P(Y = 1 | X^{(j)} = v_{1},...,X^{(d-1)} = v_{d-1})
   \end{eqnarray} 
```
or this
>    \begin{eqnarray} 
   q(v) & =&  q(v_{1},...,v_{d-1}) \nonumber \\
   & = &  P(Y = 1 | X^{(j)} = v_{1},...,X^{(d-1)} = v_{d-1})
   \end{eqnarray} 

But ofcourse, when I pasted either of above into OOoLaTeX, it spits out lots of error and just refuse to render.

Any advices please. Thanks very much.

---

### Post by hubie on 2009-03-14
I've never used OOoLaTeX, but one way to do it in LaTeX (I believe) is to use the split environment with only one ampersand at the alignment point, which would be the equals sign for your case.  So, for instance, your code would be:
```
\usepackage{amsmath}
\begin{equation}
   \begin{split}
   A + B &= C + D \\
   &= E + F  \\
   &= 3
   \end{split}
\end{equation}
```

I don't have a LaTeX environment handy to try it out, but I think that is what you do.

---

### Post by mzilhao on 2009-03-14
i never used OOoLaTeX either, but you can easily do it with LaTeX using align

```

\usepackage{amsmath}
\begin{align}
  A + B &  = C + D \\
  & = E + F \\
  & = 3
\end{align}

```

---

### Post by ad_267 on 2009-03-14
There's a good article explaining some of the different enviroments and how to use them here (pdf link): [www.tug.org/pracjourn/2006-4/madsen/madsen.pdf](www.tug.org/pracjourn/2006-4/madsen/madsen.pdf)

That applies to LaTeX but I assume you must be able to do the same in OOoLaTeX.

---

### Post by amylase on 2009-03-14
Ok I tried all three approaches

```
\usepackage{amsmath}
\begin{equation}
   \begin{split}
   A + B &= C + D \\
   &= E + F  \\
   &= 3
   \end{split}
\end{equation}
```
generates this error
> !LaTeX Error: Can be used only in preamble.
!LaTeX Error: Bad math environment delimiter.

This one 
```
\usepackage{amsmath}
\begin{align}
  A + B &  = C + D \\
  & = E + F \\
  & = 3
\end{align}
```
gave me this error message
> !LaTeX Error: Can be used only in preamble.
!Package amsmath Error:\begin{align} allowed only in paragraph mode.

I read through the madsen.pdf and tried its code, pretty much everyone caused an error.

Maybe OOoLaTeX is only able to process small snippets of LaTeX at a time and cannot understand alignment or amsmath.....

---

### Post by ad_267 on 2009-03-14
If you were to use those examples in a LaTeX document, you have to put the "\usepackage{amsmath}" before the beginning of the document (\begin{document}), is there some setting in OOoLaTeX that lets you select packages to use?

---

### Post by hubie on 2009-03-15
It looks like from the [OOoLatex page]("http://ooolatex.sourceforge.net/"), there is a *Preamble* button where you input your preamble stuff, which in this case would be ```
\usepackage{amsmath}
```

For what it's worth, the difference between using *align* and *equation/split* is that split assumes a single logical equation, so in your example that whole group would have one equation number.  It can use either *equation* or *equation**.  With align, all three lines in your equation would have a separate equation number.  This all assumes, of course, that you aren't suppressing any of the equation numbers with *\notag*, *etc*.

---

### Post by kai12 on 2009-05-08
> **amylase said:**
> 
But ofcourse, when I pasted either of above into OOoLaTeX, it spits out lots of error and just refuse to render.


hi there, 

you're code works fine if you select "Text" instead of "Inline" or "Display" (the latter two wrap your code in a math environment, which conflicts with the eqnarray environment).

cheers, kai

---

