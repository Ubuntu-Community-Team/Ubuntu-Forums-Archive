---
title: "Installing packages for TeXworks"
date: 2010-07-29
forum: Education &amp; Science
---

### Post by maurodi on 2010-07-29
Hi,

I'm doing some Software Engineering courses this year and I've installed TeXworks from the Ubuntu Software Center to help me write specifications. The program works fine as I've compiled some basic .tex files. The thing is I now want to use extra packages. I've downloaded them (.sty format), but I don't know where to put them or what to do so that the program or the compiler use them.

Thanks a lot.

EDIT: I "sudo cp" them to /usr/local/share/texmf and I ran "sudo texhash". The ls-R file there now has the package names as entries. But when I try to compile in TeXworks (in pdfLaTeX mode) it says it can't find the packages. I checked and the packages have READ permissions for everyone.

EDIT: I copied them to /usr/share/texmf-texlive/tex/latex/ instead and now it's working. I've also read that you can create ~/texmf/tex/latex/ and put the .sty there.

---

