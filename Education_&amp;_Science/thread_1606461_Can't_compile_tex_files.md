---
title: "Can't compile tex files"
date: 2010-10-26
forum: Education &amp; Science
---

### Post by ranjith19 on 2010-10-26
I am using ubuntu 10.10 (maverick meercat)

I have just installed tex-common, texlive-common, texlive-base and texlive-binaries.
I am trying to compile this simple code
[FONT="Courier New"]
\documentclass[12pt]{article}
%	options include 12pt or 11pt or 10pt
%	classes include article, report, book, letter, thesis

\title{This is the title}
\author{Author One \\ Author Two}
\date{29 February 2004}

\begin{document}
\maketitle

This is the content of this document.

This is the 2nd paragraph.
Here is an inline formula:
$   V = \frac{4 \pi r^3}{3}  $.
And appearing immediately below
is a displayed formula:
$$  V = \frac{4 \pi r^3}{3}  $$
\end{document}
[/FONT]

But when I try [FONT="Courier New"]tex /home/MY_NAME/Desktop/new.tex[/FONT] I get the following error.
[FONT="Courier New"]
This is TeX, Version 3.1415926 (TeX Live 2009/Debian)
(./new.tex
! Undefined control sequence.
l.1 \documentclass
                  [12pt]{article}
? 

[/FONT]

I have no idea what to do.

I do not want to install texlive-full package as it contains 1000 things that I will not use. I just need simple tex. I used to use Zenwalk Operating system before switching to ubuntu and it I had tetex installed in it. But now, tetex is no longer supported. So what to do?

---

### Post by FreeTheBee on 2010-10-26
You are trying to compile a latex document with TeX, try 
latex /home/MY_NAME/Desktop/new.tex  
or 
pdflatex /home/MY_NAME/Desktop/new.tex
instead.

---

### Post by ranjith19 on 2010-10-27
If I try to do that, I have to install texlive-latex-base. pdfetex returns the same error

---

### Post by NikoC on 2010-10-27
Just tried your document with Texmaker and command line pdflatex and both times a dvi document was generated without errors.

I have Ubuntu 10.10 with texlife-full installed.

---

### Post by decjedrek on 2010-10-27
Hi,

Maybe try doing the following trick. Try to modify 
```
\documentclass[12pt]{article}
``` 
to make it look like this: 
```
\documentclass{article}
\renewcommand{\normalsize}{\fontsize{12pt}{18pt}\selectfont}
``` which causes the text to 12pt high and 18pt spacing between lines

And I sugest You use ```
latex file_name.tex
```

---

### Post by ad_267 on 2010-10-27
> If I try to do that, I have to install texlive-latex-base.

You have to install the base latex package to compile a latex document... And that's a problem?

Like FreeTheBee already said, that's a LaTeX document. There's a difference between plain TeX and LaTeX and if you want to compile that document you need the texlive-latex-base package.

---

### Post by ranjith19 on 2010-10-27
I will try and post the results

---

### Post by ranjith19 on 2010-10-27
Thank you. I installed texlive-latex-base and this is what I got for [FONT="Courier New"]latex new.tex[/FONT] in the terminal.

[FONT="Courier New"]
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
(./new.tex
LaTeX2e <2009/09/24>
Babel <v3.8l> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size12.clo))
No file new.aux.
[1] (./new.aux) )
Output written on new.dvi (1 page, 960 bytes).
Transcript written on new.log.
[/FONT]

 I got the proper new.dvi.

---

### Post by nicolastraffic2 on 2010-12-08
I have just installed tex-common, texlive-common, texlive-base and texlive-binaries.
I am trying to compile this simple code
[FONT=Courier New]
[/FONT]

---

### Post by Random_Dude on 2010-12-08
> **nicolastraffic2 said:**
> I have just installed tex-common, texlive-common, texlive-base and texlive-binaries.
I am trying to compile this simple code
[FONT=Courier New]
[/FONT]

Any luck?

I find it simpler to use [Texmaker]("http://www.xm1math.net/texmaker/") instead of compiling using the terminal. It's more user-friendly. ;)

Cheers :cool:

---

### Post by d5xtgr on 2010-12-08
Does anyone know how to make evince stay in the background using TeXmaker?  When I compile a file I like to hit compile twice to catch the label changes; it really gets annoying when evince intercepts the second F1 and pops up the help menu.

---

