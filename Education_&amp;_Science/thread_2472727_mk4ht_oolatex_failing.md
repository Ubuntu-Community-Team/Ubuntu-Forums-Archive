---
title: "mk4ht oolatex failing"
date: 2022-03-10
forum: Education &amp; Science
---

### Post by xadder on 2022-03-10
Hi!
Has anyone got "mk4ht oolatex" working? When I try:

```
mk4ht oolatex tester.tex
```
 

I get:

```
System return: 0
System call: mv    sxw-tester.dir/tester.odt .
mv: cannot stat 'sxw-tester.dir/tester.odt': No such file or directory
--- Warning --- System return: 256

```
I have used this approach many years ago, but on Xubuntu 21.10 it ain't working at all.  And my latex file is as easy as can be:
```
\documentclass[12pt]{article}
\pagestyle{empty}

\begin{document}

\section{TEST 1}

testing

\end{document}

```

---

### Post by mezigy on 2022-03-11
I think you have to place your thread in another section. Education isn't the suitable one.

---

