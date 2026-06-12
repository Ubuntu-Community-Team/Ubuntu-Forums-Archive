---
title: "problem with cross referencing in lyx"
date: 2009-03-17
forum: Education &amp; Science
---

### Post by mdornfe1 on 2009-03-17
I'm writing my thesis in lyx. Whenver I try to cross reference a figure, it references the section number the figure is in not the figure number. Does anyone know how to change this, or does anybody know a message board dedicated to latex.

---

### Post by hubie on 2009-03-17
I do latex by hand, not with lyx or the other IDEs, so I don't know how much help I can give you.

Can you post your text with the reference, as well as the text that goes with the figure (if lyx lets you do that)?

In regular latex you would have a figure inserted with something like
```
\begin{figure}[here]
\includegraphics[width=0.9\textwidth]{mypic.jpg}
\caption{This is the caption to my picture.}
\label{fig:mypic1}
\end{figure}
```
and in your text you would reference it with something like
```
The figure I just inserted is referenced as Figure~\ref{fig:mypic1}.
```

You could also check out [this site]("http://www.lyx.org/Walkthrough3") to see whether you followed the necessary steps.

---

### Post by mdornfe1 on 2009-03-18
Here's an example of the code i'm using.
```
\makeatletter
\def\input@path{{/home/matthew//}}
\makeatother
\documentclass[english]{article}
\usepackage[latin9]{inputenc}
\usepackage{graphicx}
\usepackage{babel}

\begin{document}

\section{Section}


\subsection{Subsection}

I am referencing figure \ref{fig:figure}

%
\begin{figure}[h]
\includegraphics{Pictures/lab/laser}

\label{fig:figure}

\caption{This is a figure}
```
I attached the pdf output to this post. When I tell to reference the figure, it references the subsection the figure is in instead of the figure number.

---

### Post by hubie on 2009-03-19
Is that an excerpt from your example, or the whole code from the example?  The reason I ask is that I don't see an \end{figure} or \end{document}

Could you expand your example by adding a second figure to the section and/or adding another section with its own figure?  I'm curious to see whether a second figure will be referenced as 1.1, 2, or even 2.1.

---

### Post by hubie on 2009-03-19
I believe I found the answer.  I consulted my ultimate latex reference, [*The Latex Companion*]("http://www.informit.com/store/product.aspx?isbn=0201362996&aid=c9e80f0c-fab1-42b1-a79e-79453cba4ad1&rll=1") by Mittelbach and Goossens *et al.*, and they explain the issue in Section 2.4.  I can go into the details if you want, but basically within a float environment you need the \caption to come before the \label, if it doesn't, the \label command will pick up the current reference string from an entity before it, which in this case would be the Subsection.

---

### Post by mdornfe1 on 2009-03-19
> **hubie said:**
> I believe I found the answer.  I consulted my ultimate latex reference, [*The Latex Companion*]("http://www.informit.com/store/product.aspx?isbn=0201362996&aid=c9e80f0c-fab1-42b1-a79e-79453cba4ad1&rll=1") by Mittelbach and Goossens *et al.*, and they explain the issue in Section 2.4.  I can go into the details if you want, but basically within a float environment you need the \caption to come before the \label, if it doesn't, the \label command will pick up the current reference string from an entity before it, which in this case would be the Subsection.

That did it. Thanks a lot. I can't believe it was a stupid little thing like that.

---

### Post by cool.fire333 on 2009-03-29
Thank you hubie and mdornfe1.

---

### Post by theDaveTheRave on 2009-10-14
> **cool.fire333 said:**
> Thank you hubie and mdornfe1.

I second that.

that has explained a lot. I'm guessing that this is allways the case with cross references also.

David

---

### Post by tiga2001 on 2011-02-15
> **hubie said:**
> I believe I found the answer.  I consulted my ultimate latex reference, [*The Latex Companion*]("http://www.informit.com/store/product.aspx?isbn=0201362996&aid=c9e80f0c-fab1-42b1-a79e-79453cba4ad1&rll=1") by Mittelbach and Goossens *et al.*, and they explain the issue in Section 2.4.  I can go into the details if you want, but basically within a float environment you need the \caption to come before the \label, if it doesn't, the \label command will pick up the current reference string from an entity before it, which in this case would be the Subsection.

Hey, I know this thread is old, but I'd just like to say that you made my day. I, too, am using LyX and did not notice that the tutorial had their labels at the end of the caption. I was putting it in front of the figure, and the reference was giving me the subsection instead of the figure number.

---

### Post by NikoC on 2011-02-15
I don't know if this might be interesting, but you can also change how the numbering is done in lyx:

open a new document > document > settings > modules

Here you can add or remove 'number by section' for figures, equations and tables.

---

