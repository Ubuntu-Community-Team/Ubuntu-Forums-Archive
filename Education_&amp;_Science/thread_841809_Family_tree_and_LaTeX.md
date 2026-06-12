---
title: "Family tree and LaTeX?"
date: 2008-06-26
forum: Education &amp; Science
---

### Post by sol0 on 2008-06-26
Hi,

I want to create a book of my family tree in LaTeX.

First, I am **very** novice to LaTeX and are best starting with a template. Can anyone help me make a template so I can get started writing? 

I did search google and find the following:

[IMG]http://www.ursoswald.ch/LaTeXGraphics/pstricks/abb/abb39.png[/IMG]

```
\usepackage{pstricks, pstcol, pst-node, pst-tree}
\renewcommand\psedge{\nccurve}
\newcommand{\Female}[2][]{{\psset{linecolor=lightgray}\TR[#1]{\emph{#2}}}}
\newcommand{\Male}[2][]{{\psset{linecolor=black}\TR[#1]{#2}}}
\psset{nodesep=2pt, angleA=90, angleB=-90}      
\begin{document}
  \pstree[treemode=U]{\Female{{\bfseries Matilde}}}{%
    \pstree{\Male{Sebastian}}{%
      \pstree{\Male[name=P]{Philip}}{\Male{Frederick}\Female{Ethel}}
      \pstree{\Female[name=W]{Mary}}{\Male{Lionel}\Female{Agnes}}} 
    \pstree{\Female{Leonor}}{% 
      \pstree{\Male[name=R]{Ra\'ul}}{\Male{Joaquim}\Female{J\'ulia}}
      \pstree{\Female[name=A]{Am\'elia}}{\Male{\'Alvaro}\Female{Augusta}}}}
    \psset{doubleline=true, linestyle=dotted}
    \ncline{P}{W}\nbput{1940}
    \ncline{R}{A}\nbput{1954}        
\end{document}
```

Source: [http://www.ursoswald.ch/LaTeXGraphics/pstricks/pstricks.html](http://www.ursoswald.ch/LaTeXGraphics/pstricks/pstricks.html)

If anybody know or have experience with such stuff, they are welcome to write or post some good ressources. Thanks.

---

### Post by PGScooter on 2011-05-10
Did you have any succses with this? I would be curious. Are there any packages that would help? I would like to do this. I'm guessing you're not around ubuntuforums anymore, but if anyone else has an idea, I would appreciate it. Thanks

---

### Post by Lateralis on 2011-05-12
Well, this kind of stuff in Latex is difficult.  The OP posted a code snippit which makes use of the pstricks (and related) package(s) and produces something which is vaguely sensible (if a little unconventional).  

As far as I know, the only way around this would be to use pstricks.  I have no experience with this package myself, but there are plenty of resources On the web.  The link in the OP still works and looks like a decent starting point.  You may also want to look at [CTAN and the documentation contained therein]("http://www.ctan.org/search/?search=Family+tree&search_type=description"), as well as the very good documentation in the [Latex WikiBook]("http://en.wikibooks.org/wiki/LaTeX/Creating_Graphics").

If you have more specific questions I'm sure we'll be able to help, once you've had a crack at making your tree.

---

### Post by PGScooter on 2011-05-13
Lateralis, thanks for the reply. I'll post back if I end up finding a good solution.

---

### Post by not_a_phd on 2011-05-13
I would highly recommend the TikZ and PGF packages found here:

[http://sourceforge.net/projects/pgf/](http://sourceforge.net/projects/pgf/)

The the learning curve is steep, but the documentation is excellent. If you invest some time in following the tutorials in the manual, I believe that you will be able to put together a very high quality tree in Latex.

---

### Post by sol0 on 2011-05-16
> **PGScooter said:**
> Did you have any succses with this? I would be curious. Are there any packages that would help? I would like to do this. I'm guessing you're not around ubuntuforums anymore, but if anyone else has an idea, I would appreciate it. Thanks

YES, you can do it in pstricks etc, but it requires a lot of fiddling and hacking. I didn't have success with it :D 

You can look into the lifeline program instead: [http://www.math.clemson.edu/~simms/genealogy/ll/ps-anc/](http://www.math.clemson.edu/~simms/genealogy/ll/ps-anc/)

and then include it in a .tex document:

```
\documentstyle [12pt,[COLOR="lime"]psfig[/COLOR]]{article}
\pagestyle{empty}
\topmargin 0in
\textheight 7.25 in
\evensidemargin -.25in
\oddsidemargin -.25in
\textwidth 7in
\begin{document}

\twocolumn
``Nevertheless the winter wears on and death follows death.  I've tried it, 
and know how the narrowing-down feeling conflicts with the feeling of life's 
coming to a point, not a climax but a point.  At that point one must, yes, be 
selective, but not selective in one's choices if you see what I mean.  Not 
\begin{figure}[htb]
[COLOR="Lime"]\centerline{\psfig{figure=t1.ps,height=4.5in}}[/COLOR]
\caption{Alice's Ancestors}
\label{paw}
\end{figure}
choose this or that because it pleases, merely to assume the idea of choosing, 
so that some things can be left behind.  It doesn't matter which ones.  I 
could tell you about some of the things I've discarded but that wouldn't help 
you because you must choose your own, or rather not choose them but let them 
be inflicted on and off you.  This is the point of the narrowing-down 
process.  And gradually, as the air gets thinner as you climb a mountain, 
these things will stand forth in a relief all their own --- the look of 
belonging.  It is a marvelous job to do, and it is enough just to approximate 
it.  Things will do the rest.  Only then will the point of not having 
everything become apparent, and it will flash on you with such dexterity and 
such terribleness that you will wonder how you lived before --- as though a 
valley hundreds of miles in length and full of orchards and all sorts of 
benevolent irregularities of landscape were suddenly to open at your feet, 
just as you told yourself you could not climb a step higher.  This casual, 
poorly seen new environment (but how gladly you are aware of imperfect vision, 
this time!) is to be a new kind of arbitrariness for you, one that protects 
and promotes without ever leaving the time-inflicted lesions of the old, 
toward which you struggled so hard without knowing it.  These are vanished 
with the saw-toothed anomalies of time itself, and an open, moist, impregnable 
order of the day --- kind, generous and protective --- surrounds you as the 
artless gestures of a beautiful girl surround her with nobility which may 
never be detected, the fountain of one's life.  And one never need wish to 
see it, for its truth does not matter, and is unimaginable.''

--- excerpt from John Ashbery's  ``The New Spirit'' (in Three Poems)
 
\end{document}

```

and then customize the style for your layout..

Source: op. cit.

---

### Post by kbaumen on 2011-05-21
+1 for tikz.

It's a very versatile graphics package for LaTeX. The graphics it produces are really good quality. And also, a bit off-topic but worth mentioning imo, Gnuplot (starting from v4.4) has a tikz terminal which really gives you some production quality graphics. I use this combination for all my coursework at uni.

I am neither associated with tikz, nor gnuplot btw. :D

---

