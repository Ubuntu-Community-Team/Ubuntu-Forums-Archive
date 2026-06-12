---
title: "Bibtex linewidth"
date: 2011-07-05
forum: Education &amp; Science
---

### Post by mJayk on 2011-07-05
Hay,

Im busy writing my dissertation and it is required to be double spaced.  Thats fine ive got the main text body double spaced using  

\linespread{1.75}


My only problem is the line spacing also seams to continue into the references list which i create via using a .bib file.  I would like to set the line spacing back to 1 for the reference list but dont have a clue where to start.  Google yields no help so i'm kind of stuck.  Currently using texworks if its any help.


Thanks in advance 


Matt

---

### Post by sisyphus1978 on 2011-07-05
Best place for TeX advice is [http://tex.stackexchange.com](http://tex.stackexchange.com)

My understanding is that your way of doing it is outdated. I use the setspace package

```
\usepackage{setspace}
```then use:
```

\onehalfspacing %set onehalf spacing or
\doublespacing %set double spacing
```If refs aren't singlespace after that, try something like this:

```
\begin{singlespace}
\bibliography{refs}
\end{singlespace}
```Good luck.

---

### Post by mJayk on 2011-07-05
Thanks shall try that, I always try to avoid packages if i can get away with it :)

M

---

