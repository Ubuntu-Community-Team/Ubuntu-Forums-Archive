---
title: "Need help with latex/bibtex"
date: 2008-03-01
forum: Education &amp; Science
---

### Post by slimdog360 on 2008-03-01
Im just testing the waters with this for the moment as Im seeing if this would be good to use to write my thesis. Im trying this out in OSX using Texshop as the latex editor and Bibdesk as a frontend to bibtex.

Basically I've made a latex document with a reference in it. Then made a reference list using bibdesk. I've got them in the same folder (is this what you are supposed to do?) 

But then when I tell texshop to make the pdf I get a question mark where my reference should be and a page at the end with the heading 'Bibliography' but no references under it.

here is the latex file
```
\documentclass[a4paper,12pt]{book}
\usepackage{cite}
\begin{document}

\title{something}
\author{me}
\date{2nd March 2008}
\maketitle

\begin{equation}
z(w,z) = \int{\sin(x)}dx
\end{equation}
pretend reference \cite{Lang:2000}

\bibliography{references}
\bibliographystyle{apa}
\end{document}
```

and here is the bibtex file which is created by bibdesk, which I titled references.
```
@conference{Lang:2000,
	Address = {Athens, Greece},
	Author = {J.H. Lang},
	Booktitle = {Something else},
	Date-Added = {2008-03-02 10:59:35 +1100},
	Date-Modified = {2008-03-02 12:50:43 +1100},
	Pages = {20-30},
	Read = {No},
	Title = {Something},
	Year = {2000}}
```

Can anyone help me

---

### Post by zgornel on 2008-03-02
Is the references file called "references.bib" ? Everything looks ok ...

---

### Post by hugmenot on 2008-03-02
Does your OSX LaTeX frontend run the stuff often enough to get the references resolved? If you would do it by hand you would have to rerun latex (and bibtex) a few times until it got everything sorted.

---

### Post by hugmenot on 2008-03-02
No, no, your example above is a little shaky.

First, I think \usepackage{cite} [does not do what you think it does]("http://www.ctan.org/tex-archive/macros/latex/contrib/cite/")
```
cite.sty       Compressed, sorted lists of numerical citations: [8,11-16]
```
Normally, if you want "Author Year" citation you use natbib. For normal, numbered citations [1],[2] you don't need any package here.

Then you specify "apa" as the bibliography style. Do you have an actual bibstyle called "apa.bst"? There are a few different APA bibstyles. The multitude is a little confusing. There is a full-blown APA conformant package called apacite. I myself have simply used newapa.bst in the past, but that one is not really APA, I guess.

The quickest fix to your example is this:
```

\documentclass{book}
\usepackage{apacite}
\begin{document}
\title{something}
\author{me}
\date{2nd March 2008}
\maketitle

\begin{equation}
z(w,z) = \int{\sin(x)}dx
\end{equation}
pretend reference \cite{Lang:2000}
\bibliographystyle{apacite}
\bibliography{references}
\end{document}

```

BTW, the book class is perhaps not the right one for a thesis. You may want to check out memoir.cls or KOMA-Script's scrrprt.cls.

---

### Post by perroazul on 2009-02-23
@slimdog360: you question is old but this might help somebody. suppose your document is called 'thesis.tex'
first you compile your document: latex thesis
(no extension necessary)
then you run bibtex on it: bibtex thesis
then you run latex again (two times). and that's it. I use emacs+auctex which is a very good environment for typing latex documents (I only have to click buttons to run those commands, no need of using a command line)
cheers

---

### Post by colsandurz on 2009-06-01
indeed perroazul, your post just helped me quite a bit :)

---

### Post by durand on 2011-02-27
Thanks perroazul, that was a helpful post!

---

