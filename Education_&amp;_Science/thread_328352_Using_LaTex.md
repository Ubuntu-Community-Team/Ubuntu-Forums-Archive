---
title: "Using LaTex"
date: 2006-12-30
forum: Education &amp; Science
---

### Post by nyxynyx on 2006-12-30
Hello! Im wondering whether using Kile is sufficient, or do I need Texlive, because I see the 2 Howtos in this forum on LaTeX and they seem to install Kile with Texlive. I installed Kile only and seem to be able to produce Latex documents. Whats Texlive for then? Thanks!:D

---

### Post by harishg on 2006-12-30
> **nyxynyx said:**
> Hello! Im wondering whether using Kile is sufficient, or do I need Texlive, because I see the 2 Howtos in this forum on LaTeX and they seem to install Kile with Texlive. I installed Kile only and seem to be able to produce Latex documents. Whats Texlive for then? Thanks!:D

The version of latex running on linux (tetex) does not have the full version of latex in it.So if you need some files you might need to install them and then configure with texhash. Texlive is a full version of tex which can also be run directly from a CD.It was usually supplied to people in the tex users group.

If you need a frontend to latex without the need to type in all the latex commands, I would suggest you to try using Lyx.

---

### Post by slaanco on 2006-12-31
i was using lyx for some time, but i switched to kile. I can type equations faster in kile, then in lyx, and also i have full control about what i'm typing. LyX is usefull for beginners, but still very good also for the advanced users, it depends what kind of text r u writing. :cool:

---

### Post by neoflight on 2007-01-01
> **nyxynyx said:**
> Hello! Im wondering whether using Kile is sufficient, or do I need Texlive, because I see the 2 Howtos in this forum on LaTeX and they seem to install Kile with Texlive. I installed Kile only and seem to be able to produce Latex documents. Whats Texlive for then? Thanks!:D

texlive, tetex, miketex etc can be considered as latex installations. 

texmaker, kile, etc are frontends and/or IDE 's that help to organise source codes, and provide simple shortcuts to compile and convert source codes.

in linux, IMO, kile+texlive, texmaker+texlive, gedit+texlive are good way to produce latex documents. hope this clarifies....

---

### Post by Zizo on 2007-01-14
Hi, 
 
I want to do something like this 
 
1.3 Section title 
1.3.1 Subsection title 
  //this is working fine 
 
In this subsection (1.3.1) I want to have 
 
 Bullet --Title 
  - Graph 
  - Table related to the graph 
 
 Bullet --Title 
  - Graph 
  - Table related to the graph 
 
1.3.2 
   Bullet 
     etc.... 
   Bullet 
     etc 
 
My code looks like this:

\section{Performance}
\setcounter{secnumdepth}{6}

\subsection{Latency}
bla bla bla

\subsubsection{On machine xxxx}

\begin{itemize}
\item TCP

\begin{figure}[htb]
\begin{minipage}[b]{0.5\linewidth} % A minipage that covers half the page
\includegraphics[width=7cm,height=7cm]{file a}
\caption{caption}
\label{fig:label}
\end{minipage}
\hspace{0.7cm} % To get a little bit of space between the figures
\begin{minipage}[b]{0.5\linewidth}
\includegraphics[width=7cm,height=7cm]{file b}
\caption{caption}}
\label{fig:label}
\end{minipage}
\end{figure}

\begin{table}[h!b!p!]
\caption{caption}
\begin{tabular}{|*{7}{p{2cm}|}}
\hline
2 & 0.57 &  0.017 & 0.1 & 1750 & 0.28 & 3500 \\ 
\hline
14 & 4 & 1.05 & 1.02 & 214 & 2.33 & 428 \\ 
\hline
40 & 13 & 8672 & 93 & 74 & 6.74 & 148 \\
\hline
\end{tabular}
\label{table-latency-on-rdr28}
\end{table}
\end{itemize}

If I add another code like this (bullet pluts figure plus table) the positions are messed up.

I have the graphs and the tables but the bullets and the tables positions are getting messed up. The first table is always going under the second bullted list, it must go under the first. 
 
P.S. A table reflects the data in the graph plot. so they must be close to each other, 
 
How can I solve this?  I am not sure this is the right place to post this question. I am using kile on ubuntu.
 
Thank you in advance

---

### Post by harishg on 2007-01-19
One option is using [hbtp] for both images and tables.This might make them stick to where you want them to be.Another option might be to use the wrapfig package.( google it)

---

