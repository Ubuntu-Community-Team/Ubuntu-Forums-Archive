---
title: "Text mining in R - installing tm package"
date: 2010-12-13
forum: Education &amp; Science
---

### Post by JGT on 2010-12-13
Hi

I'm having little luck installing the tm (text mining) package in R.


```
> install.packages("tm")
```

gives me (after choosing a mirror)

```
Warning message:
In getDependencies(pkgs, dependencies, available, lib) :
  package ‘tm’ is not available
```

According to the website [http://cran.ma.imperial.ac.uk]("http://cran.ma.imperial.ac.uk"), I can choose a task view.
```

> install.packages("ctv")
> library("ctv")
> install.views("NaturalLanguageProcessing")
```

but I can't get further than:

```
In getDependencies(pkgs, dependencies, available, lib) :
  package ‘ctv’ is not available
```

I tried dropping the downloaded tm folder (and later the compressed archive) in the R lib directory /home/john/R/i486-pc-linux-gnu-library/2.10 and installing it manually, but I can't seem to do this either. Help appreciated.

---

### Post by hubie on 2010-12-13
What version are you running?  I tried installing the package on my system (Jaunty) and I got the same error.  I noticed that my default ubuntu package was at version 2.8.1, while the tm package required >= 2.11.0.  I followed the [update instructions here]("http://cran.r-project.org/bin/linux/ubuntu/README") by adding the appropriate repository to my apt sources and it now installs fine for me.  I made sure to install both the r-base package as well as the r-base-dev package.

---

### Post by JGT on 2010-12-14
Thanks - I'll try tonight when I get back. The lib directory is 2.10 so that could well be the version number and the source of the problem.

---

### Post by JGT on 2010-12-14
That works - many thanks!

---

### Post by hubie on 2010-12-14
And my thanks to you.  Until I saw your post I never thought to add the R repository to my system.  Now I don't need to wait for newer versions to be backported.

---

