---
title: "Installing texlive without the documentation"
date: 2010-02-17
forum: Education &amp; Science
---

### Post by vynot on 2010-02-17
Hi,
    I hardly ever look at the offline documentation for texlive.. my first step is to check online.  So I wonder if it is possible to install texlive on ubuntu without the documentation.  I first thought that it was the texlive package that pulled in the doc dependencies, so I installed the individual packages leaving out the doc packages.  But they still get installed.  My internet connection is not very fast so I try to keep useless downloading to a minimum.  
    I am not sure how to modify the given dependencies of a package, nor sure if that is all it takes.  Any ideas?

Thanks.

---

### Post by SchighSchagh on 2012-03-23
Bump. You can uninstall the -doc packages after you install the actual package you want in order to save disk space, but you still waste time downloading useless stuff. Seriously, everybody just googles documentation these days. Nobody uses offline documentation anymore!

---

### Post by Stefan_K on 2012-04-12
> **SchighSchagh said:**
> Seriously, everybody just googles documentation these days. Nobody uses offline documentation anymore!

I don't agree. I use
```
texdoc packagename
```
(or an alias) at the command line to quickly open the documentation immediately. I don't google and browse possibly outdated matches.

Perhaps users who don't know texdoc might think entering a package name or a phrase into google search might be the quickest.

As you don't install documentation on your local system, you might be interested in [TeXdoc Online]("http://texdoc.net"), which provides online access to the complete TeX Live documentation,
[LIST]
[*]via a search field
[*]as shortlink like [http://texdoc.net/pkg/hyperref](http://texdoc.net/pkg/hyperref)
[*]via a quick search field such as in the top right corner of Firefox
[/LIST]

Actually, texdoc.net was originally built for [LaTeX-Community.org]("http://latex-community.org"), so that writers can link a package name or an alias to the documentation via a simple button click or bbcode, which is easily possible because of the generic texdoc link syntax which runs the actual texdoc query on the server.

Stefan

---

