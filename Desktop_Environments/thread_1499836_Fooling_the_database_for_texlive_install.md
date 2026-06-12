---
title: "Fooling the database for texlive install"
date: 2010-06-02
forum: Desktop Environments
---

### Post by FunkyRes on 2010-06-02
I have texlive installed on its own partition in /opt

In rhel, I can fool the rpm database by having a dummy package that provides the various tex dependencies allowing me to install packages like emacs-auctex without needing to pull in the entire latex package system.

This is important. I have several texlive installs IE some older documents of mine were created with texlive 2005 and won't compile in 2009 without changes to the source, so minor edits need to be done in 2005 environment, but modern docs I do in modern tex, I just update my path to specify which texlive install is active, hence I don't want to use linux vendor packaged tex because I need to make sure I have a tex version installed that compiles source I may need to do a minor edit on 17 years from now.

But I do want to use things like vendor packaged emacs, and the auctex extension to emacs doesn't really giver a rats posterior end what version of tex is installed. In rhel I know how to do this, I just make a small rpm that tells the database it provides the dependencies things like auctex and lyx want. How do I do that in ubuntu?

---

