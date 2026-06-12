---
title: "Where to store bibtex .bst files"
date: 2005-11-01
forum: Desktop Environments
---

### Post by DocFox on 2005-11-01
I have prepared some custom bibliography styles for use with Bibtex/latex, and would like to store them in my ~/ directory if possible.

Having browsed a little, I made a /texmf/ folder and ran *sudo texhash*.

I now have:
> ben@nutmeg:~$ cat texmf/ls-R
% ls-R -- filename database for kpathsea; do not change this line.
./:
.:
ls-R
NewEngland.bst


But when I run bibtex i get
> ben@nutmeg:~/medicine/research/CO2$ bibtex proposal
This is BibTeX, Version 0.99c (Web2C 7.4.5)
The top-level auxiliary file: proposal.aux
I couldn't open style file NewEngland.bst
---line 23 of file proposal.aux
 : \bibstyle{NewEngland
 :                     }
I'm skipping whatever remains of this command
I found no style file---while reading file proposal.aux
(There were 2 error messages)


I've also tried copying my bst file to : /usr/local/share/texmf/tex/latex/
and running *texhash*. No joy.

So what's a man to do?

---

### Post by DocFox on 2005-11-01
Found this command:
> 
ben@nutmeg:/usr/local/share/texmf/tex$ kpsewhich --show-path bst
.:/home/ben/texmf/bibtex/bst//:!!/usr/local/share/texmf/bibtex/bst//:!!/usr/local/lib/texmf/bibtex/bst//:!!/var/lib/texmf/bibtex/bst//:!!/usr/share/texmf/bibtex/bst//:/home/ben/texmf/bibtex///:!!/usr/local/share/texmf/bibtex///:!!/usr/local/lib/texmf/bibtex///:!!/var/lib/texmf/bibtex///:!!/usr/share/texmf/bibtex///


So I ran mkdir ~/texmf/bibtex
copied the bst file to there, reran [FONT="Courier New"]texhash[/FONT] and it works.

:razz: 

ben

---

