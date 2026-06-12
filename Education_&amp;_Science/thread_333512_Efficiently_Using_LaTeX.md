---
title: "Efficiently Using LaTeX"
date: 2007-01-07
forum: Education &amp; Science
---

### Post by commike37 on 2007-01-07
Recently, I read an article about a class at Harvard called Math 55 where they teach four years of undergraduate math in a year-long course.  One of the interesting things I noticed in the article is that the students prefer to type up their homework using LaTeX.  That idea perked my interest, so I installed TeTeX and Kile from Synaptic Package Manager (in Ubuntu Dapper).  Once I learned LaTeX, I typed up the detailed solution to two partial differential equations and was quite impressed by LaTeX's capabilities.  However, there was one caveat:  it took forever to do.

I understand that with time and experience, I can become much more efficient using LaTeX, but even then it would seem much more slower than just writing it out by hand.  I can justify some loss of efficiency because of the very professional look of the homework and the experience I would gain with LaTeX, but there's still a gap to be bridged.

First, does someone know how to do a line break in 'displaymath'?  I couldn't figure it out, so I just put the equations in an 'equation*' and start a new 'equation*' when I want a new line.  I did try an 'eqnarray*', but the formatting it gave me was very odd (I often put several steps of the same solution on one line).

Also, I would like to create some keyboard shortcuts for things I frequently type:  Greek characters such as \lambda, the integral symbol \int, the curly d in a partial derivative \partial, etc.  If I had a library of these shortcuts, over time I could memorize them and type everything up much faster.

Also, this is kind of unrelated, but does someone know how to widen the margins?  Page layout is very complicated, and every try to get 1" margins all around has failed.  I try to keep the margins small so I can use paper efficiently.

---

### Post by Steveire on 2007-01-07
I don't think I can help with the equation problem I'm afraid. Have you read the not short guide to latex?

To get kile to complete those greek letters, go to Settings > Configure Kile > Kile > Complete > Tex/Latex (tab) > Add (button)

select the file latex-mathsymbols.cwl

I use this kind of thing to sort out my page margins:
```

% Page geometry
\setlength{\textwidth}{14.5cm}
\setlength{\textheight}{23cm}
\setlength{\topmargin}{-0.5cm}
\setlength{\oddsidemargin}{1.25cm}
\textfloatsep=0.5cm

```

---

### Post by commike37 on 2007-01-07
Thanks for the help.  I did read the first 3 chapters as well as the section in Chapter 6 on page layout.  The problem with 'displaymath' is that it seems to resist line breaks.  Your idea works for the layout, but I actually found a really good solution on the web before I saw your post.
```
\usepackage{fullpage}
```
More detailed information (as well as the trick I just showed) can be found here
[[COLOR="Blue"]http://web.mit.edu/answers/latex/formatting/latex_margins.html[/COLOR]]("http://web.mit.edu/answers/latex/formatting/latex_margins.html")

Adding in completion for the math symbols is another step forward.  I still would like if there's a way to do keyboard shortcuts to paste custom phrases such as "\begin{equation*}\end{equation*}" or "\frac{\partial y}{\partial x}".

---

### Post by Steveire on 2007-01-08
Well it's not entirely convenient, but you can use abbreviations for those things if you want.

Make a file at  /usr/share/apps/kile/complete/abbreviation/myAbbrevs.cwl with
```

# My abbreviations file
# 8.1.2007
estar=\begin{equation*}\end{equation*}
pderiv=\frac{\partial y}{\partial x}

```
Then go to the abbreviations tab in the same settings page as before, and add that file. Then in your latex document, you begin typing estar and type ctrl+alt+spacebar, and it offers the expanded abbreviation. Alternatively, you could add 
```

\begin{equation*}
\frac{\partial y}{\partial x}

```

to /usr/share/apps/kile/complete/tex/latex-document.cwl and tick the box at 

Settings > Latex > Environments > Automatically complete environments

Restart Kile, and begin{equation*} will be a completion option, and the end{equation*} will be automatically inserted.

---

### Post by neoflight on 2007-01-08
> **commike37 said:**
> First, does someone know how to do a line break in 'displaymath'? 

use ```
\\
``` to break line inside... or use like below...
otherway
enclose the expression within $ signs after including amsmath package 
```
\include{amsmath}
$ a^2 + 2*a*b + b^2 $. \\ 
```

> Also, I would like to create some keyboard shortcuts for things I frequently type:  Greek characters such as \lambda, the integral symbol \int, the curly d in a partial derivative \partial, etc.  If I had a library of these shortcuts, over time I could memorize them and type everything up much faster.
not exaclty and answer. keyboard shortcuts ==> editor stuff. but in the source code if you want to use a command instead of some long-words used repeatedly..for example.."i like ubuntu" 
use \newcommand command
eg:
```
\newcommand{\ilu}{I like ubuntu} 
```:mrgreen:

then use the shortcut command inside the source code...

> Also, this is kind of unrelated, but does someone know how to widen the margins?  Page layout is very complicated, and every try to get 1" margins all around has failed.  I try to keep the margins small so I can use paper efficiently.

include a new package called geometry.
```
\usepackage[left=1in,right=1in,top=1in,bottom=1in]{geometry}
```

hope this helps...

search for lshort.pdf in google and download that very helpful latex guide...its oxygen!

---

### Post by commike37 on 2007-01-08
New commands and abbreviations both sound like good ideas.  I'll try them both.

However, \\ doesn't work in math mode.  Math mode will ignore most spaces and line breaks (I've also tried \newline and \linebreak).  The problem with $...$ is that math formulae in text mode are typeset differently.  The sample page I made in LaTeX has one formula in both math mode and text mode, and the one in math mode is considerably better.

I'm pretty sure I have all the margin issues taken care of.  I thought that none of this was working at first, but then I realized I had to run 'texconfig' from the terminal and set the default paper to letter.  Apparently, TeTeX would create an A4 page even if I had letterpaper specified in the document class.  That was what was making the commands not work as I had hoped.

---

### Post by Miguel on 2007-01-09
Have a look at \begin{eqnarray}. This allows line breaks (with \\) and also allows centering with respect to e.g. an equal sign. There is a way to have only the last line numbered. I don't know if there is an equivalent displaymath command (matharray???). Example:

```

\begin{eqnarray}\label{eq:superH}
H & = & \sum_{i}\frac{\mn{p}_i^{\phantom{i}2}}{2m_e} + \sum_{I}\frac{\mn{P}_I^{\phantom{i}2}}{2M_I} -  \frac{1}{4\pi\epsilon _0} \sum_{i,J}\frac{z_Je^2}{|r_i-R_J|} + \nonumber\\
 & + & \frac{1}{2} \frac{1}{4\pi\epsilon _0}  \sum_{i\neq j}\frac{e^2}{|r_i-r_j|} + \frac{1}{2}\frac{1}{4\pi\epsilon _0}  \sum_{I\neq J}\frac{z_Iz_Je^2}{|R_I-R_J|}\quad .
\end{eqnarray}

```

Try it to see if you like it. Please note that I might have used an abbreviation here (taken from my halfway PhD work, with quite some abbreviations).

---

### Post by troy7777 on 2007-01-09
> **Miguel said:**
> Have a look at \begin{eqnarray}. This allows line breaks (with \\) and also allows centering with respect to e.g. an equal sign. There is a way to have only the 

<snip>



try to avoid eqnarray/* environment when you can. try align instead. this page explains why: [http://dw.tug.org/pracjourn/2006-4/madsen/madsen.pdf](http://dw.tug.org/pracjourn/2006-4/madsen/madsen.pdf)

hth

---

### Post by kleeman on 2007-01-09
If you want to be a lazy slob like me use lyx instead of raw latex. I wrote my doctoral thesis with latex (mathematical physics) and it was hard going. Since then I forgot all the latex because I was using Scientific Word. When I started on linux again I found lyx a great way to spin up again on latex and a great memory saver. You can export to latex once you are done with lyx and then fine tune this using latex style files etc.

---

### Post by Lux Perpetua on 2007-01-10
> **commike37 said:**
> First, does someone know how to do a line break in 'displaymath'?  I couldn't figure it out, so I just put the equations in an 'equation*' and start a new 'equation*' when I want a new line.  I did try an 'eqnarray*', but the formatting it gave me was very odd (I often put several steps of the same solution on one line).Have a look at this document: [http://www.ctan.org/tex-archive/macros/latex/required/amslatex/math/amsldoc.pdf](http://www.ctan.org/tex-archive/macros/latex/required/amslatex/math/amsldoc.pdf). I'm a fan of environments align and align*, which make it easy to typeset a sequence of equations or inequalities with each step on a different line. If you don't care about alignment, there are gather and gather*.

---

### Post by commike37 on 2007-01-10
Perfect, \begin{gather*} is exactly what I'm looking for.

---

### Post by TeKniKal on 2007-01-12
I love working with LaTeX like you too, and this is what I put in most of my documents to get better margins:

```
\setlength{\voffset}{-2cm}
  \addtolength{\textheight}{2cm}
  \addtolength{\textwidth}{3cm}
  \addtolength{\hoffset}{-1.5cm}
```
That should work if you use the A4paper-class :-) (for letter size paper, I wouldn't know).

I also have a full file of common abbreviations (commands/environments), some are in Dutch (as I'm Flemish), and they are mostly mathematical, mechanical or chemical shortcuts. Perhaps you have some use for these. You can include them into your own files by putting them in the pre-able or by referring to them by saving the file in the same folder as your document (let's say commands.inc.tex) and then typing \input{commands.inc.tex} in your document's pre-amble.

```
% Egon Geerardyn common latex Commands
%
% 2007 01 03 : Version 0.5
%

% dutch arc-goniometric functions
    \newcommand{\bgsin}{\mbox{\textsf{Bgsin}}\,}
    \newcommand{\bgcos}{\mbox{\textsf{Bgcos}}\,}
    \newcommand{\bgtan}{\mbox{\textsf{Bgtan}}\,}
    \newcommand{\bgcot}{\mbox{\textsf{Bgcot}}\,}

%alternative notation for arc-goniometric functions
    \newcommand{\argcos}{\mbox{\textsf{argcos}}\,}
    \newcommand{\argsin}{\mbox{\textsf{argsin}}\,}
    \newcommand{\argtan}{\mbox{\textsf{argtan}}\,}
    \newcommand{\argcot}{\mbox{\textsf{argcot}}\,}
    
%alternative notation for arc-hyperbolic functions
    \newcommand{\argcosh}{\mbox{\textsf{argcosh}}\,}
    \newcommand{\argsinh}{\mbox{\textsf{argsinh}}\,}
    \newcommand{\argtanh}{\mbox{\textsf{argtanh}}\,}
    \newcommand{\argcoth}{\mbox{\textsf{argcoth}}\,} 
    
% coordinaat   
    \newcommand{\co}{\mbox{ \textsf{co}}\,}
% absolute waarde
    \newcommand{\abs}[1]{\left| #1 \right|}
% degree symbol
    \newcommand{\degree}[0]{^\circ}

% ronde B voor bol
    \newcommand{\bol}[0]{\mathscr{B}}

% ronde K voor kwadriek
    \newcommand{\kwadriek}[0]{\mathscr{K}}

%differentials
    \renewcommand{\d}[1]{\;\textsf{d}#1}
    \newcommand{\pd}[1]{\partial #1}
    \newcommand{\D}{\;\textsf{D}}

%dot and double dot for D_t en D_t^2
    \newcommand{\dt}[1]{\dot{#1}} %dot notation for d/dt
    \newcommand{\dtt}[1]{\ddot{#1}} % double dot notation for d^2 / dt^2

%accent (acute) for D_s and D_s^2
    \newcommand{\ds}[1]{#1 \acute{}\,} % accent notation for d/ds
    \newcommand{\dss}[1]{#1 \acute{}\, \acute{}\,} % double accent notation for d^2 / ds^2

%accent notation for arbitrrary derivative of order 1 or 2
    \newcommand{\dx}[1]{#1 \grave{}\,} % accent notation for arbitrary d / dx
    \newcommand{\dxx}[1]{#1 \grave{} \, \grave{}\,} % double accent notation for d^2 / dx^2

%norm of a vector
    \newcommand{\norm}[1]{\left\| #1 \right\|}

%infinity redeclariation for use with WikiPedia LaTeX notation
    \newcommand{\infin}{\infty}

%Probability notation
    \newcommand{\prob}[1]{P\left(#1\right)}

%vector functions 
    % vector notation
    \newcommand{\vect}[1]{\overline{#1}} %large notation
    %(scalar product, <>-notation
    \newcommand{\scalprod}[2]{\left\langle #1,#2 \right\rangle}
    \newcommand{\scalprodv}[2]{\scalprod{\vec{#1}}{\vec{#2}}} %includes vector arrows
    \newcommand{\scalprodV}[2]{\scalprod{\vect{#1}}{\vect{#2}}}
    %vectorr product
    \newcommand{\vectprod}[2]{\left( #1 \times #2 \right)}
    \newcommand{\vectprodv}[2]{\vectprod{\vec{#1}}{\vec{#2}}} % includes vector arrows
    \newcommand{\vectprodV}[2]{\vectprod{\vect{#1}}{\vect{#2}}}
    %gradient, rotatie, divergentie
    \newcommand{\Dgrad}[1]{\textsf{grad}\,#1\;}
    \newcommand{\Ddiv}[1]{\textsf{div}\,#1\;}
    \newcommand{\Drot}[1]{\textsf{rot}\,#1\;}
%chemistry
    %concentration
    \newcommand{\conc}[1]{\left[ #1 \right]}
    %equilibrum arrows
    \newcommand{\evenwicht}{\rightleftharpoons}
    \newcommand{\reactie}{\rightarrow}
    %reactieconstante
    \newcommand{\K}{\,\textsf{K}}
    \newcommand{\Q}{\,\textsf{Q}}
    %p-notations
    \newcommand{\pH}{\,\textsf{pH}}
    \newcommand{\pOH}{\,\textsf{pOH}}
    \newcommand{\pK}{\,\textsf{pK}}
    \newcommand{\pKa}{\pK_A}
    \newcommand{\pKb}{\pK_B}
    \newcommand{\pKw}{\pK_W}
    %eenheden
    \newcommand{\eenheid}[1]{\,\textsf{#1}\,}
    \newcommand{\eenh}[1]{\eenheid{#1}}
```

---

### Post by Kadin2048 on 2007-05-29
I think that the best way to do multiline equations is definitely the align environment:

```
\begin{align}
x & = y \\
y & = x
\end{align}
```

Should produce two equations, closely spaced, with the "&" used as the alignment point. That way you can do really nicely aligned equations, not just centered ones.

---

### Post by Zdravko on 2007-05-30
> **neoflight said:**
> 
include a new package called geometry.
```
\usepackage[left=1in,right=1in,top=1in,bottom=1in]{geometry}
```hope this helps...


I'll definitely try that! :) Hope it works!

---

### Post by mohring on 2012-11-23
Dear Stievire,

this is an inquiry about defining abbreviations in kile. According to the documentation it should be possible to insert newline by %n and the curser by %C. However, expanding my abbreviation just inserts the text as it is, i.e. %n introduces a comment rather than creating a newline.
Could you give me a hint? (encoding, kile version, ...)

Best regards
Jan Mohring

---

### Post by howefield on 2012-11-23
Old thread back to sleep.

Please start a new thread if required.

---

