---
title: "LaTeX Help"
date: 2009-04-15
forum: General Help
---

### Post by chiefbutz on 2009-04-15
I am using just the normal *latex* command in linux and I am wondering if there is a default place local to the user where it looks for .sty files other than the current directory. Thank you.

---

### Post by stumbleUpon on 2009-04-15
create a directory named texmf, inside that a directory called tex and inside that a directory called latex. Put all your cutom style file (.sty) files in there. When you run texhash, it will look for a directory namned texmf in your home folder. If found all the .sty files will be recognized

---

### Post by Stefan_K on 2009-04-17
Hi,

I would expect ~/texmf as the default user tex directory. Try [kpsewhich]("http://texblog.net/hypertext-help/latex-tools/kpsewhich/") in the terminal/ on the command line:
```
kpsewhich -var-value=TEXMFHOME
```
The output should be the desired value.

Stefan


--
[TeXblog.net]("http://texblog.net")

---

