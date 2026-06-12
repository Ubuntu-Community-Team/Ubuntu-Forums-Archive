---
title: "latex packages under karmic"
date: 2009-11-19
forum: Education &amp; Science
---

### Post by Micronaut on 2009-11-19
Hello,

I've installed texlive on karmic.  I have documents I've written using jaunty that no longer build in karmic due to missing packages.  All the packages are present in /usr/share/texmf-texlive/tex/latex and various other texmf folders and I have run texhash several times (with sudo). Is anybody else having problems with latex not seeing packages in karmic, or have any solutions?

texshade, siunitx, and setspace are a particular problem, 2 of which are meant to be included in the texlive extra packages.

Thanks for any assistance.

---

### Post by diesch on 2009-11-19
```
\documentclass[a4paper]{article}
\usepackage{texshade, setspace}
\begin{document}
foo
\end{document}
```
works for me. 

Where did you put *siunitx*?

---

### Post by jhsdluiash on 2009-11-20
Its related to relational database You will have to read RDMS to understand this:popcorn:

---

### Post by Micronaut on 2009-11-20
> **diesch said:**
> ```
\documentclass[a4paper]{article}
\usepackage{texshade, setspace}
\begin{document}
foo
\end{document}
```
works for me. 

Where did you put *siunitx*?

My distrubution seem to be picking up the texshade package but is reporting "undefined control sequence \end{texshade}" which doesn't make sense as it understands \begin{texshade}.

I put the siunitx package in /usr/share/texmf-texlive/tex/latex as this was the only place it seemed to get picked up by texhash.  

Thanks for your help.

---

### Post by diesch on 2009-11-20
> **Micronaut said:**
> My distrubution seem to be picking up the texshade package but is reporting "undefined control sequence \end{texshade}" which doesn't make sense as it understands \begin{texshade}.

I guess it gets confused by something between *\begin{texshade}* and *\end{texshade}*

> **Micronaut said:**
> 
I put the siunitx package in /usr/share/texmf-texlive/tex/latex as this was the only place it seemed to get picked up by texhash.  


*~/texmf/tex/latex* or* /usr/local/share/texmf/tex/latex *are better places for manually installed packges, but */usr/share/texmf-texlive/tex/latex* should work, too.

What does
```
kpsewhere siunitx.sty
```
print?

---

### Post by Micronaut on 2009-11-21
> **diesch said:**
> I guess it gets confused by something between *\begin{texshade}* and *\end{texshade}*



*~/texmf/tex/latex* or* /usr/local/share/texmf/tex/latex *are better places for manually installed packges, but */usr/share/texmf-texlive/tex/latex* should work, too.

What does
```
kpsewhere siunitx.sty
```
print?

The command returns:
/usr/share/texmf-texlive/tex/latex/siunitx/tex/latex/siunitx/siunitx.sty


LaTeX seems to be getting through siunitx with it stored in the usr/share/texmf-texlife/tex/latex folder, but getting hung up on the texshade issue.  From the error log file texshade is reading the command \begin{texshade} but is then not understanding the file parameters after it.  Texshade requires the format \begin{texshade}{filename}

E.g,  my text contains \begin{texshade}{./file-path/file.aln} LaTeX is reading the filename as a command and not a path to the file for analysis, but texshade requires \texshade{filename}, so I'm a bit confused.  It compiles on Windows using MikTeX so I am wondering if there is a missing package, or some error with the texshade package in ubuntu.  

Here's some of the error message it produces:

(./sequencing/pfus1mod.aln:
LaTeX Font Info: Try loading font information for T1+cmss on input line 19.
(/usr/share/texmf-texlive/tex/latex/base/t1cmss.fd
File: t1cmss.fd 1999/05/25 v2.5h Standard LaTeX font definitions
) .
! Undefined control sequence.
\iterate ...e \innerloopcount by \csname \prefix@
mw\first@ \endcsname \expa...
l.19 \end{texshade}
\label{pfus1modalign}
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.
! Missing number, treated as zero.
<to be read again>
\mwT
l.19 \end{texshade}
\label{pfus1modalign}
A number should have been here; I inserted `0'.
(If you can't figure out why I needed to see a number,
look up `weird error' in the index to The TeXbook.)
! Undefined control sequence.

(the pfus1modalign stuff is my filename to load in to texshade, the paths and files are all present and correct... as far as I can tell)

The error message then replicates itself for each letter in the filename path (everything inside the {./path to file/file}).

Thanks for your assistance with my problem, much appreciated.

---

### Post by Micronaut on 2009-11-24
\end{texshade}
A number should have been here; I inserted `0'.
(If you can't figure out why I needed to see a number,
look up `weird error' in the index to The TeXbook.)
! Undefined control sequence.

????  Has anybody experienced the texshade package no longer recognising the \end{texshade} function??:confused:

---

### Post by Micronaut on 2009-11-24
i'm completely lost so I removed the texshade package from ubuntu and copied my own from the ctan database, but of course it isn't seen by texhash in any of the normal directories for some unknown reason.

I copied it to /usr/share/texmf-texlive/tex/latex/texshade but texmaker reports it's can't find texshade.sty.  :confused:

still hunting for a solution....

---

### Post by Micronaut on 2009-11-26
Fixed.

Re-installed texshade from the ctan database, re-compiled texshade.sty and the document is now rending.

Maybe some problem with the packaged texshade under Karmic, but can't be sure as as I made many modifications trying to get it to work.

---

