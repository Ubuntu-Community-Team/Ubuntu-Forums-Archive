---
title: "LaTeX tensor package problem"
date: 2007-05-03
forum: Education &amp; Science
---

### Post by Berkut on 2007-05-03
I started using Latex a few days ago, but am making good progress. I can't figure this one out though, so I hope someone can help me out.

I need an index on the left side (left superscript). I found that some people use "{}^a x", but this looks really bad with capital italic letters. The package "tensor" which is in "texlive-math-extra.deb" should be used for such cases (found on google tex groups) but I can't make it work. In this example

```

\documentclass{article}
\usepackage{tensor}
\begin{document}
\tensor*[^{14}_6]{C}{}
\end{document}

```

the output is: "Package tensor Error: Sub/Superscript token missing.".

Hope some Latex users can help!

*Franci*

---

### Post by WW on 2007-05-03
Use tensor in math mode, e.g.
```

\documentclass{article}
\usepackage{tensor}
\begin{document}
$\tensor*[^{14}_6]{C}{}$
\end{document}

```

---

### Post by Berkut on 2007-05-04
I'm sorry, but I wrote it wrong here in the forum. I get the same output with math mode. Can someone try it on their computer, if they get the same result?

---

### Post by jfinkels on 2007-05-04
For the small amount of LaTeX that I've done, I have used "The Not So Short Introduction to LaTeX 2&#949;" (search for it, it's out there), and the way they format left superscripts are like this:
```

{}^{12}\textrm{C}

```
That's carbon-12. It looks fine, I think.

---

### Post by WW on 2007-05-04
The math-mode example worked for me, but I am using tetex (in ubuntu 6.06)  with the tensor package from here: [http://www.ctan.org/tex-archive/macros/latex/contrib/tensor/](http://www.ctan.org/tex-archive/macros/latex/contrib/tensor/)

---

