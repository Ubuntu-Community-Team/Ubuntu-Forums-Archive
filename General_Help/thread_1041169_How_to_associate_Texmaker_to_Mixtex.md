---
title: "How to associate Texmaker to Mixtex"
date: 2009-01-16
forum: General Help
---

### Post by FreakyBug on 2009-01-16
Hi folks

I am using Ubuntu 804 and installed Texmaker and miktex for linux.

Then, I typed "mpm --install=newPACKAGE" and then "sudo texhash" in terminal. But still Texmaker reported an error of missing the package I just installed when compiling my LaTeX files. Anyone can give me a hint on how to handle this?

---

### Post by king.pest on 2009-01-16
wow, I didn't even know it's possible to have miktex on linux. I know this isn't answering your question, but why wouldn't you want to use texlive deb packages from the universe repository?
and if you really have to use miktex, try to see if your env variables are set correctly (TEXMFMAIN, TEXMFDIST, TEXMFLOCAL, TEXMFSYSCONFIG, etc.), although I've no idea which of them miktex uses.

---

