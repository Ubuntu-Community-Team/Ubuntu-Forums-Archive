---
title: "cleaning up my system"
date: 2005-10-02
forum: Desktop Environments
---

### Post by abandoned_hussam on 2005-10-02
I'm trying to clean up my kubuntu system. I found those packages that are not dependancies of other packages. 
Are these packages safe to remove? 
texinfo texi2html python2.4-numarray lapack3

---

### Post by xtacocorex on 2005-10-02
I know that texinfo and texihtml go with LaTex or are used by it if needed. Lapack is a linear algebra library, from what I remember when I used to run Fedora [Anaconda tells you what the packages are if you go that deep into custom installation]. I don't know about the python one.

I'd say that if you don't use LaTex, you could get rid of those two. I don't think I've found anything that uses lapack.

I could be wrong though.

---

### Post by abandoned_hussam on 2005-10-02
Ok, I removed them.
What about those?
openjade, docbook-dsssl and docbook-to-man. Nothing seems to depend on them.

---

### Post by xtacocorex on 2005-10-02
Don't know what openjade is nor do I know what docbook-dsssl is.

I do think docbook is a means to write code documentation for projects, and therefore docbook-to-man probably converts docbook stuff to man pages.

---

### Post by Martin Witte on 2005-10-02
When you want to know more on a package: synaptic can show descriptions and a lot more information on packages, or you can use apt-cache show <package name>

---

