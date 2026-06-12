---
title: "Problem displaying greek in Latex with babel&amp;inputenc"
date: 2011-03-23
forum: Education &amp; Science
---

### Post by Eypros on 2011-03-23
Hello to everybody,

Well this is my first post. I am trying to write my thesis in greek and I am facing a (strange in my opinion) problem with greek text. My thesis will be using greek and english text interchangebly so I need both. I was able to write greek using xeTex but I need to use a template which uses babel. Something in the following form.

\[usepackage]("http://www.golatex.de/wiki/index.php?title=%5Cusepackage")[english, greek]{babel}
\[usepackage]("http://www.golatex.de/wiki/index.php?title=%5Cusepackage")[iso-8859-7]{inputenc}
  
I had managed to make it work on winXP but I hope to achieve it also in Xubuntu as I prefer to work in linux environment. I also don't want to write latin text in latex for appearing as greek (like in the example below before latintext command)

I have tried something as simple as:

```
\[documentclass]("http://www.golatex.de/wiki/index.php?title=%5Cdocumentclass"){article}
\[usepackage]("http://www.golatex.de/wiki/index.php?title=%5Cusepackage")[english, greek]{babel}
\[usepackage]("http://www.golatex.de/wiki/index.php?title=%5Cusepackage")[iso-8859-7]{inputenc}

\begin{document}
abgdezhjiklmnxoprs(c)tufqyw

\latintext Latin text 
\greektext &#917;&#955;&#955;&#951;&#957;&#953;&#954;&#972; &#954;&#949;&#943;&#956;&#949;&#957;&#959;
\end{document}
```and there was no error message (process exited normally) but the result in pdf
was without the text after ```
\greektext
``` command.

I am using Texmaker and I have installed plenty of packages.

Any possible ideas of the problem? Is it a font issue?

Anyway thanks for any (future) reply!

---

