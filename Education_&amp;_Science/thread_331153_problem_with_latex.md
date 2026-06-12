---
title: "problem with latex"
date: 2007-01-04
forum: Education &amp; Science
---

### Post by levin on 2007-01-04
I have used MikTeX before and I am now trying to get hold of latex in Ubuntu.  First of all, I am not using Kile nor LyX. I am using the "gedit-terminal" combo. I write my tex files in gedit then compile it in the terminal. By doing so, I have no problem getting the basics (such as articles and reports) done. However, I have problems with installing new .cls files. 

I am trying to use res.cls for my resume. I understand that I have to have res.cls installed. I downloaded it from CTAN and I have copy and paste it into /usr/share/texmf-tetex/tex/latex/base. However, when I do "latex myCV.tex" in the terminal, in return, I get the error message > "! LaTeX Error: File `res.cls' not found." I found a way to get around it, which is to specifically state where is "res.cls". I know there must be a more efficient way to get around this, if not, I think I will have nightmares compiling a tex file with tens of additional packages/styles/fonts. 

Any help would be appreciated.

---

### Post by gagatz on 2007-01-04
I suppose, that it is sufficient, but not very elegant, to put the required scripts into the directory where your .tex file is. At least that worked for me.

---

### Post by neoflight on 2007-01-04
> **levin said:**
> I have used MikTeX before and I am now trying to get hold of latex in Ubuntu.  First of all, I am not using Kile nor LyX. I am using the "gedit-terminal" combo. I write my tex files in gedit then compile it in the terminal. By doing so, I have no problem getting the basics (such as articles and reports) done. However, I have problems with installing new .cls files. 

I am trying to use res.cls for my resume. I understand that I have to have res.cls installed. I downloaded it from CTAN and I have copy and paste it into /usr/share/texmf-tetex/tex/latex/base. However, when I do "latex myCV.tex" in the terminal, in return, I get the error message I found a way to get around it, which is to specifically state where is "res.cls". I know there must be a more efficient way to get around this, if not, I think I will have nightmares compiling a tex file with tens of additional packages/styles/fonts. 

Any help would be appreciated.

run texhash and texconfig after you install a cls, sty files...

---

### Post by parktownprawn on 2007-01-04
see 

[https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

---

### Post by levin on 2007-01-05
Ah.. I have missed out this documentation. Thanks for the help everyone and sorry for the time-wasting.. ;)

---

