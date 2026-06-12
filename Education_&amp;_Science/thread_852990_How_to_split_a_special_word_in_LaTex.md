---
title: "How to split a special word in LaTex"
date: 2008-07-08
forum: Education &amp; Science
---

### Post by zigmund on 2008-07-08
Hello everybody,

I have a problem in LaTex. I have to split a special word to avoid the Overfull error. The word is  similar to internet address:

 
*plugins/org.eclipse.rcp. source. <os> . <ws>.<arch> \_ X.X.X. <version>/src/*

So I tried to obtain the result throught the \url{} command and then the \- ( which must create some preferential split-point) but anything changed. Anybody have any advice?

tanks

---

### Post by hugmenot on 2008-07-08
I guess you should wrap the code into a codebox. The package [FONT="Courier New"]listings[/FONT] is nice for this:

```
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage[english]{babel}
\usepackage{listings}
\begin{document}

\begin{lstlisting}[language=Java,breaklines=true]
	plugins/org.eclipse.rcp.source.<os>.<ws>.<arch>\_X.X.X.<version>/src/
\end{lstlisting}

\end{document}
```

---

### Post by zigmund on 2008-07-08
Tanks for your reply. The packages listings seems to me very usefull but I have some problem in using it: when I compile the .tex file the compiler show an error message that said that *Couldn't load requested language*.

 Do you think that  I have been doing a wrong installation of listings?

Despite your advice is very usefull it didn't resolv the problem because the string isn't in programming language but is a generalization address of local folder.

---

### Post by hugmenot on 2008-07-08
The language doesn't really matter. You can omit this parameter.
It will try do detect the language, but it is not necessary. The language definitions only cause some more formatting to happen. Just read the documentation about it.
The important thing is, that you can break the code into short lines.
Tip: there's also \lstinline[breaklines=true]'veryveryverylongline' , with this you can embed some code into the text body

---

