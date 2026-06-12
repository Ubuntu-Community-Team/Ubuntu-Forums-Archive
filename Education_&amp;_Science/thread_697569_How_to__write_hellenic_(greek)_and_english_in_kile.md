---
title: "How to : write hellenic (greek) and english in kile latex"
date: 2008-02-15
forum: Education &amp; Science
---

### Post by Claus7 on 2008-02-15
Hello,

I was trying to find out how to write both hellenic and english in the same latex / kile document. I had made it work in the past, yet I didn't remember the procedure in my new installation in gutsy. I have to say that my effort focused only on modern greek (monotonic).

The only thing I used was synaptic package manager so as to install the necessary files. I didn't install anything by myself. The only thing I had to do afterwards was to include the necessary packages via usepackage command in kile.

So open synaptic and install the following packages :
[LIST]
[*]kile  
[*]latex-beamer
[*]latex-cjk-common
[*]latex-mk
[*]**latex-ucs**  
[*]latex-ucs-contrib
[*]latex-xcolor
[*]linuxdoc-tools
[*]linuxdoc-tools-latex
[*]pgf
[*]preview-latex-style
[*]texlive-base
[*]texlive-base-bin
[*]texlive-extra-utils
[*]**texlive-latex-base**
[*]**texlive-latex-extra**
[*]texlive-latex-recommended
[*]texlive-pictures

[*]kbabel
[*]kbabel-dev
[*]kpdf
[*]texlive-lang-greek
[/LIST]

With all the above I was able to write and also inlude pictures without any problem. When I opened kile the packages I used were the following :

\documentclass[a4paper,11pt]{article}
\usepackage{epsfig}
\usepackage{rotating}
\usepackage{ucs}
\usepackage[english,greek]{babel}
**\usepackage[utf8x]{inputenc}**
\usepackage{overpic}
[B]\newcommand{\gr}{\selectlanguage{greek}}
\newcommand{\en}{\selectlanguage{english}} [/B]

With the *\usepackage[english,greek]{babel}* the default language is the hellenic one. So if someone wants to write in english, someone has to do the following :
{\en *english text...*}

And that's it! 

There might be out there better solutions. This is how I was able to write flawlessly. The list of the packages I provide might be long, yet while I was searching I might have installed also packages that were not really needed. Also I have to inform that the encoding down on the left hand side of the kile program is utf-8. The pdflatex display worked nicely.

I hope this is helpful,
Regards!

---

### Post by sotiriss on 2008-02-22
Thanks a lot man! It really helped me. I had problem with package greektex, but now i can write in greek.
Thanks, Sotiris

---

### Post by Dionysios on 2008-04-27
Thank you my friend, very helpful post.

---

### Post by tekkenlord on 2008-05-28
Thanks for the post. Users interested in the greektex package can also check this tutorial:

[http://ubuntuforums.org/showthread.php?p=5061066#post5061066]("http://ubuntuforums.org/showthread.php?p=5061066#post5061066")

---

### Post by simosx on 2008-11-21
A new popular way to type Unicode (including Greek) in TeX is to use xetex.
Some instructions are available at
[http://ubuntu.opengr.net/viewtopic.php?f=9&t=930](http://ubuntu.opengr.net/viewtopic.php?f=9&t=930)

---

