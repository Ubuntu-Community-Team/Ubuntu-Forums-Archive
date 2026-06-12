---
title: "powerdot paintings style"
date: 2007-03-22
forum: Education &amp; Science
---

### Post by xadder on 2007-03-22
I just installed texlive and powerdot for making LaTeX slide presentations, after using (and very much liking)  prosper for years.

I wanted a style without table of contents, but didn't see one among the provided style files. The user manual suggested paintings as such a style, so I have downloaded that from CTAN. But now I get:

(/usr/share/texmf-texlive/tex/latex/psnfss/times.sty)
(/usr/share/texmf-texlive/tex/latex/psnfss/pifont.sty
(/usr/share/texmf-texlive/tex/latex/psnfss/upzd.fd)
(/usr/share/texmf-texlive/tex/latex/psnfss/upsy.fd))
! Undefined control sequence.
<recently read> \pddefinepalettes 
                                  
l.31 \pddefinepalettes
                      {Syndics}{% Rembrandt van Rijn: "The Syndics" - 1662
? 


Has anybody got this working? I notice that this style, along with several others, is mentioned in the manual, but not part of the Ubuntu texlive installation.

Thanks

---

### Post by rjerrard on 2007-06-05
> **xadder said:**
> I just installed texlive and powerdot for making LaTeX slide presentations, after using (and very much liking)  prosper for years.

I wanted a style without table of contents, but didn't see one among the provided style files. The user manual suggested paintings as such a style, so I have downloaded that from CTAN. But now I get:

(/usr/share/texmf-texlive/tex/latex/psnfss/times.sty)
(/usr/share/texmf-texlive/tex/latex/psnfss/pifont.sty
(/usr/share/texmf-texlive/tex/latex/psnfss/upzd.fd)
(/usr/share/texmf-texlive/tex/latex/psnfss/upsy.fd))
! Undefined control sequence.
<recently read> \pddefinepalettes 
                                  
l.31 \pddefinepalettes
                      {Syndics}{% Rembrandt van Rijn: "The Syndics" - 1662
? 


Has anybody got this working? I notice that this style, along with several others, is mentioned in the manual, but not part of the Ubuntu texlive installation.

Thanks
I have just run into the swame issue of notbeing able to latex a document using powderdot due to an undefined error message:

! Undefined control sequence.
<recently read> \pddefinepalettes
l.31 \pddefinepalettes

However the original post on this by xadder was never responded to. Does anyone know how to fix this?

Thanks for any help, Bob
--
Dr.Robert Jerrard
Dept of Math and Comp Sci
Concordia University College of Alberta
Edmonton, Alberta

---

### Post by rjerrard on 2007-06-05
> **rjerrard said:**
> I have just run into the swame issue of notbeing able to latex a document using powderdot due to an undefined error message:

! Undefined control sequence.
<recently read> \pddefinepalettes
l.31 \pddefinepalettes

However the original post on this by xadder was never responded to. Does anyone know how to fix this?

Thanks for any help, Bob
--
Dr.Robert Jerrard
Dept of Math and Comp Sci
Concordia University College of Alberta
Edmonton, Alberta
The problem is solved, the versions of powerdot.cls and the powerdot-*.sty files are too old in texlive. When you download the newer ones from ctan and put them in the correct directory, for me /usr/share/texmf-texlive/tex/latex/powerdot, them run mktexlsr (don't forget sudo) then the powerdot document latexs just fine.

Hope this helps others

---

