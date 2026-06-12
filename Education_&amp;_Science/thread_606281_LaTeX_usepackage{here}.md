---
title: "LaTeX \usepackage{here}"
date: 2007-11-07
forum: Education &amp; Science
---

### Post by one_ro on 2007-11-07
Hi all,

Could anyone tell me how to install the package "here" in LaTeX?
(using Kubuntu Gutsy, I believe I have installe the tetex-live distribution).

Thanks in advance,
Adrian

---

### Post by mali2297 on 2007-11-08
That package seems to be obsolete. I suggest that you use the **float** package instead. Then you can stop a figure from floating with the option [H]:
```

\usepackage{float}
.
.
.
\begin{figure}[H]
.
.
\end{figure} 
.
.
.

```
(Likewise for tables etc.)

CTAN about [float]("http://www.ctan.org/tex-archive/help/Catalogue/entries/float.html"):
> The package also provides the H float modifier option of the obsolete here  package.

---

### Post by one_ro on 2007-11-08
Oh, so that was why I couldn't find it... :)
Many, many thanks,
Adrian

---

### Post by QuITh on 2007-11-25
That's all I need, thanks.

---

### Post by rophys on 2012-11-09
Hello all,

I'm trying to put some figures in the right places in text but is not working.

I'm using the following packages:
\usepackage{graphicx}
\usepackage{natbib}
\usepackage{float}
\usepackage{varioref}
\usepackage{wrapfig}
\usepackage{dcolumn}
\usepackage{subfigure}
\usepackage{subfigmat}
\usepackage{fancyvrb}
\usepackage{floatrow}

When I compiled the text, the figure is not going to the right position and also is appearing the symbol [t!] close to the figure. I've tried everything =/

This is the code I'm using to place the figure :

\begin{figure}[t!]
\begin{center}
\includegraphics[keepaspectratio,width=13cm]{figures/introduction/cavity.eps}
\end{center}
\caption{}
\label{fig}
\end{figure} 

Many thanks

---

### Post by overdrank on 2012-11-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

