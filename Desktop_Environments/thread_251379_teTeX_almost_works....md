---
title: "teTeX almost works..."
date: 2006-09-05
forum: Desktop Environments
---

### Post by nmsb on 2006-09-05
Hi!

I've just installed teTeX (tetex-base, tetex-bin, tetex-extra and tetex-common) on my iBook (no MacOS X, just Ubuntu 6.06), but I'm getting the following problem.

I have some macros in nmsb.sty and one picture (EPS) that I use often.  So I copied them to /home/nmsb/texmf.  Using texconfig, after rehash, I checked that TEXMFHOME has indeed the value /home/nmsb/texmf.  Everything seems OK!

Then, to test the installation, I compile the following LaTeX file (ola.tex)

----- Start of ola.tex -----
\documentclass{nmsb}
\usepackage{nmsb}
\begin{document}
Ol\'a mundo!
\end{document}
----- End of ola.tex -----

and get the following error:

----- Start of error -----
~/Desktop$ latex ola.tex
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./ola.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo))

! LaTeX Error: File `nmsb.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name:
----- End of error -----

I haven't yet found anything (Google, Forums, etc) that helped me to fix this problem.  Any ideas?

TIA

-- 
Nuno Miguel dos Santos Baeta
ille nihil dubitat quem nulla scientia dictat

---

### Post by Najand on 2006-09-05
> **nmsb said:**
> Hi!

I've just installed teTeX (tetex-base, tetex-bin, tetex-extra and tetex-common) on my iBook (no MacOS X, just Ubuntu 6.06), but I'm getting the following problem.

I have some macros in nmsb.sty and one picture (EPS) that I use often.  So I copied them to /home/nmsb/texmf.  Using texconfig, after rehash, I checked that TEXMFHOME has indeed the value /home/nmsb/texmf.  Everything seems OK!

Then, to test the installation, I compile the following LaTeX file (ola.tex)

----- Start of ola.tex -----
\documentclass{nmsb}
\usepackage{nmsb}
\begin{document}
Ol\'a mundo!
\end{document}
----- End of ola.tex -----

and get the following error:

----- Start of error -----
~/Desktop$ latex ola.tex
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./ola.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo))

! LaTeX Error: File `nmsb.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name:
----- End of error -----

I haven't yet found anything (Google, Forums, etc) that helped me to fix this problem.  Any ideas?

TIA

-- 
Nuno Miguel dos Santos Baeta
ille nihil dubitat quem nulla scientia dictat

It is obviously not a tetex problem. You just don't have the TEX style `nmsb.sty' installed. IF you have it installed, refresh your tetex and try it again.

---

### Post by galv on 2006-09-05
Hello,
If you copy the ``nmsb.sty'' file to the dir you are working (in this case "Desktop") it should work.

---

### Post by Najand on 2006-09-05
> **galv said:**
> Hello,
If you copy the ``nmsb.sty'' file to the dir you are working (in this case "Desktop") it should work.

Well, I don't usuaully use other classes and styles except IEEEproc , but I think to install (add) new styles and classes in Tetex you need to add it to some directries under $VARTEXMF/tex/latex/ directory. If I am misunderstood please forgive me in advance.

---

### Post by nmsb on 2006-09-05
Hello!

> **galv said:**
> Hello,
If you copy the ``nmsb.sty'' file to the dir you are working (in this case "Desktop") it should work.

It works, but I don't want to have copies of the same files, e.g., nmsb.sty, in several directories.  I just want to have one copy!

---

### Post by nmsb on 2006-09-05
Hello!

> **Najand said:**
> It is obviously not a tetex problem. You just don't have the TEX style `nmsb.sty' installed. IF you have it installed, refresh your tetex and try it again.

I agree with you, it is not a teTeX problem.

BTW, nmsb.sty is just a collection os macros I use often (there isn't any nmsb.ins).  If I rename it nmsb.tex and use \input instead of \usepackage, the problem remains.

If refresh = rehash (Am I wrong?), then I did refresh teTeX and it created an ls-R file in my /home/nmsb/texmf directory.

----- Start of ls-R -----
% ls-R -- filename database for kpathsea; do not change this line.
./:
.:
ccm.tex
ls-R
nmsb.sty
nmsb.tex
ubi.eps
univ.tex
----- End of ls-R -----

(nmsb.sty is a copy of nmsb.tex, or vice-versa.  I created both to check if anything was wrong.)

I have a (very) old laptop (Toshiba Satellite Pro 470CDT) running GNU/Debian 2.x and I don't have (yes, it still works) this problem.  I had the same problem and the solution was a line in .bashrc such as

     export TEXINPUTS=....

This solution doesn't work with the iBook, probably because of different versions of teTeX.

Any ideas?

TIA

---

