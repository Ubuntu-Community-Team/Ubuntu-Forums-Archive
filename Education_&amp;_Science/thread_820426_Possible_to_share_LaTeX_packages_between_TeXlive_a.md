---
title: "Possible to share LaTeX packages between TeXlive and MikTeX?"
date: 2008-06-06
forum: Education &amp; Science
---

### Post by Mander on 2008-06-06
In noodling around on my dual-boot system (Vista/Hardy) today looking for a package that I downloaded into MiKTeX, it occurred to me that I have an awful lot of duplication between it and TeXlive.  

The actual package files are the same for either OS, right?  Is it possible to point both programs to a custom location on another partition and share that information, like you can for Firefox/Thunderbird profiles?  

That way, if I fiddle with something in one OS then switch to the other for some reason, I wouldn't have to go through all my packages and check that they are up to date.

---

### Post by hugmenot on 2008-06-06
Yes, you can.

You could edit /etc/texmf/texmf.d/05TeXMF.cnf and change the path to your local TEXMF tree.

```
% A place for local additions to a "standard" texmf tree.
% This tree is not used for local configuration maintained by
% texconfig, it uses TEXMFCONFIG below.
TEXMFLOCAL = /usr/local/share/texmf
```


run »sudo update-texmf« and »sudo texhash« afterwards.

---

